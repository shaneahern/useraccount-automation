Title: Automating User Account Management

Problem Statement:

As an IT Administrator, you are responsible for managing user accounts in your organization. You have noticed that the process of creating, updating, and deleting user accounts is repetitive and time-consuming. To improve efficiency, you decide to create a script that automates these common tasks.

Your task is to create a Python script that allows you to manage user accounts in a simple and automated way. The script should be able to perform the following actions:

1. Create a new user account with the following details:
    - First Name
    - Last Name
    - Email Address
    - Username
    - Password
2. Update an existing user account with new details.
3. Delete a user account.
4. List all user accounts.

For the purpose of this exercise, you can store user account data in a Python dictionary, where the keys are the usernames, and the values are another dictionary containing the user's details (first name, last name, email address, and password).

Function Signature:
```
def manage_user_accounts(
  action: str,
  username: str = None,
  first_name: str = None,
  last_name: str = None,
  email: str = None,
  password: str = None
) -> Union[None, str, Dict[str, Dict[str, str]]]:
```

**Input**
- `action`: The action to be performed. It should be one of the following: "create", "update", "delete", or "list".
- `username`: The username of the user account (used for actions "update", "delete", and "create").
- `first_name`: The first name of the user account (used for actions "create" and "update").
- `last_name`: The last name of the user account (used for actions "create" and "update").
- `email`: The email address of the user account (used for actions "create" and "update").
- `password`: The password of the user account (used for actions "create" and "update").

**Output**
- For "create", "update", and "delete" actions, return a string message indicating the status of the operation.
- For the "list" action, return a dictionary containing all user accounts.

**Examples**
```python
accounts = manage_user_accounts("create", username="jsmith", first_name="John", last_name="Smith", email="john.smith@example.com", password="secret")
assert accounts == "User account 'jsmith' created successfully."

accounts = manage_user_accounts("create", username="adoe", first_name="Alice", last_name="Doe", email="alice.doe@example.com", password="mypassword")
assert accounts == "User account 'adoe' created successfully."

accounts = manage_user_accounts("list")
assert accounts == {
    "jsmith": {
        "first_name": "John",
        "last_name": "Smith",
        "email": "john.smith@example.com",
        "password": "secret"
    },
    "adoe": {
        "first_name": "Alice",
        "last_name": "Doe",
        "email": "alice.doe@example.com",
        "password": "mypassword"
    }
}

accounts = manage_user_accounts("update", username="jsmith", first_name="Johnny", email="johnny.smith@example.com")
assert accounts == "User account 'jsmith' updated successfully."

accounts = manage_user_accounts("list")
assert accounts == {
    "jsmith": {
        "first_name": "Johnny",
        "last_name": "Smith",
        "email": "johnny.smith@example.com",
        "password": "secret"
    },
    "adoe": {
        "first_name": "Alice",
        "last_name": "Doe",
        "email": "alice.doe@example.com",
        "password": "mypassword"
    }
}

accounts = manage_user_accounts("delete", username="adoe")
assert accounts == "User account 'adoe' deleted successfully."

accounts = manage_user_accounts("list")
assert accounts == {
    "jsmith": {
        "first_name": "Johnny",
        "last_name": "Smith",
        "email": "johnny.smith@example.com",
        "password": "secret"
    }
}
```

**Notes**
- Ensure that you validate the input for each action and handle any errors accordingly.
- Implement the script using functions to separate the different actions and make the code more readable and maintainable
