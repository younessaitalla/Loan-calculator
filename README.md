# Loan-calculator

# main code

import argparse
import math

# Initialize the parser
parser = argparse.ArgumentParser(description='Loan Calculator')

# Add the parameters positional/optional
parser.add_argument("--type", help="Define the loan type ")
parser.add_argument("--principal", help="The value of the loan principal", type=float)
parser.add_argument("--periods", help="The number of months in which repayments will be made.", type=int)
parser.add_argument("--interest", help="Nominal interest rate.", type=float)
parser.add_argument("--payment", help="The annuity payment", type=float)

# Parse the arguments
args = parser.parse_args()
if args.type == "diff":
    if args.principal:
        pass
        if args.periods:
            pass
            if args.interest:
                pass
                i = args.interest / (12 * 100)
                sum_D = 0
                for m in range(1, args.periods + 1):
                    D = args.principal / args.periods + i * (args.principal - (args.principal * (m - 1)) / args.periods)
                    print("Month", m, "payment is", math.ceil(D))
                    sum_D += math.ceil(D)
                print("Overpayment =", round(sum_D - args.principal))
            else:
                print("Incorrect parameters.")
        else:
            print("Incorrect parameters.")
    else:
        print("Incorrect parameters.")
if args.type == "annuity":
    if args.principal:
        pass
        if args.periods:
            pass
            if args.interest:
                pass
                if args.payment is None:
                    pass
                    i = args.interest / (12 * 100)
                    # print(i)
                    A = args.principal * (i * math.pow(1 + i, args.periods) / (math.pow(1 + i, args.periods) - 1))
                    A_ceil = math.ceil(A)
                    print("Your annuity payment = {}!".format(A_ceil))
                    print("Overpayment =", math.ceil(A_ceil * args.periods - args.principal))
                else:
                    print("Incorrect parameters.")
            else:
                print("Incorrect parameters.")
        else:
            print("Incorrect parameters.")
    else:
        print("Incorrect parameters.")

    if args.principal:
        pass
        if args.interest:
            pass
            if args.payment:
                pass
                if args.periods is None:
                    pass
                    i = args.interest / (12 * 100)
                    n = math.log(args.payment / (args.payment - i * args.principal), 1 + i)
                    if n % 10 != 0:
                        N = math.ceil(n)
                        # print(divmod(N, 12))
                        if N % 12 != 0:
                            print("It will take {} years and {} months to repay this loan!".format(N // 12, N % 12))
                        else:
                            print("It will take {} years to repay this loan!".format(N // 12))
                    print("Overpayment =", round(args.payment * N - args.principal))
                else:
                    print("Incorrect parameters.")
            else:
                print("Incorrect parameters.")
        else:
            print("Incorrect parameters.")
    else:
        print("Incorrect parameters.")

    if args.payment:
        pass
        if args.periods:
            pass
            if args.interest:
                pass
                if args.principal is None:
                    pass
                    i = args.interest / (12 * 100)
                    P = args.payment / (i * (1 + i) ** args.periods / ((1 + i) ** args.periods - 1))
                    print("Your loan principal = {}!".format(math.floor(P)))
                    print("Overpayment =", math.ceil(args.payment * args.periods - P))
                else:
                    print("Incorrect parameters.")
            else:
                print("Incorrect parameters.")
        else:
            print("Incorrect parameters.")
    else:
        print("Incorrect parameters.")
