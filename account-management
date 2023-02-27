# Objectives
# improving the student's skills in operating with the getter, setter
# and deleter methods;
# improving the student's skills in creating their own exceptions.
# Scenario
# Implement a class representing an account exception,
# Implement a class representing a single bank account,
# This class should control access to the account number and account balance
# attributes by implementing the properties:
# it should be possible to read the account number only, not change it.
# In case someone tries to change the account number, raise an alarm by
# raising an exception;
# it should not be possible to set a negative balance. In case someone
# tries to set a negative balance, raise an alarm by raising an exception;
# when the bank operation (deposit or withdrawal) is above 100.000, then
# additional message should be printed on the standard output (screen)
# for auditing purposes;
# it should not be possible to delete an account as long as the balance
# is not zero;
# test your class behavior by:
# setting the balance to 1000;
# trying to set the balance to -200;
# trying to set a new value for the account number;
# trying to deposit 1.000.000;
# trying to delete the account attribute containing a non-zero balance.

class AccountException(Exception):
    pass


class BankAccount:

    def __init__(self, number, balance):
        self.__account_number = number
        self.__account_balance = balance

    @property
    def account_number(self):
        return self.__account_number

    @account_number.setter
    def account_number(self, value):
        raise AccountException("Invalid operation")

    @account_number.deleter
    def account_number(self):
        if self.account_balance == 0:
            del self
        else:
            raise AccountException('Not possible to cancel an account with '
                                   'a non zero balance')

    @property
    def account_balance(self):
        return self.__account_balance

    @ account_balance.setter
    def account_balance(self, value):
        if value < 0:
            raise AccountException("The balance can not be negative")
        elif value > 100000:
            raise AccountException("The amount exceeded the single deposit "
                                   "limit, your account will be frozen"
                                   " for auditing purposes")
        else:
            self.__account_balance = value


# create account
account_1 = BankAccount('0001', 0)
print("Account created. Account number: {}, balance: {}".format(
    account_1.account_number, account_1.account_balance))

# set balance to 1000
account_1.account_balance += 1000
print(account_1.account_balance)

# set balance to -200
try:
    account_1.account_balance = -200
except AccountException as e:
    print(e)

# try to change account number
try:
    account_1.account_number = "003"
except AccountException as e:
    print(e)


# deposit 1000000
try:
    account_1.account_balance += 1000000
except AccountException as e:
    print(e)

# try to delete attribute with a non zero balance
try:
    del account_1.account_number
except AccountException as e:
    print(e)

# outputs...
# Account create. Account number: 0001, balance: 0
# Account balance 1000
# The balance can not be negative
# Invalid action
# The amount exceeded the single deposit limit, your account will be
# frozen for auditing purposes
# Not possible to cancel an account with a non zero balance
