### Project: Simple Password Manager

#### Overview:
This project is a basic command-line password manager implemented in Python. It allows users to securely store and retrieve passwords for different services. The passwords are encrypted before storage to ensure security.

#### Installation:
1. Clone the repository:
   ```
   git clone https://github.com/your-username/password-manager.git
   ```

2. Navigate to the project directory:
   ```
   cd password-manager
   ```

3. Install the required dependencies:
   ```
   pip install cryptography
   ```

#### Usage:
1. Run the password manager script:
   ```
   python password_manager.py
   ```

2. Follow the on-screen instructions to perform actions such as adding new passwords, retrieving passwords, and listing all stored passwords.

#### Libraries Used:
- **cryptography**: This library provides cryptographic recipes and primitives. In this project, we use the `Fernet` symmetric encryption tool from this library to encrypt and decrypt passwords securely.
- **os**: This library provides a portable way of using operating system-dependent functionality. We use it to handle file operations and check for the existence of files.

#### Code Explanation:

##### `PasswordManager` class:
This class encapsulates the functionality of the password manager. It handles encryption, decryption, saving passwords to a file, retrieving passwords from the file, and listing all stored passwords.

- `__init__`: Initializes the password manager and loads the encryption key from a file or generates a new one if it doesn't exist. The `Fernet` key is used for symmetric encryption and decryption.
  
- `load_key`: Loads the encryption key from a file. If the key file exists, it reads the key from the file. Otherwise, it generates a new key and saves it to the file for future use.
  
- `encrypt_password`: Encrypts a password using the loaded key. It initializes a `Fernet` instance with the key and encrypts the password using the `encrypt` method. The encrypted password is returned as a base64-encoded string.
  
- `decrypt_password`: Decrypts an encrypted password using the loaded key. It initializes a `Fernet` instance with the key and decrypts the password using the `decrypt` method. The decrypted password is returned as a plain string.
  
- `save_password`: Saves a password entry to a file after encrypting it. It takes the service name, username, and password as input, encrypts the password, and writes the encrypted password along with the service name and username to the password file.
  
- `get_password`: Retrieves a password from the file and decrypts it. It takes the service name and username as input, reads the encrypted password corresponding to the service and username from the password file, decrypts it, and returns the plain password.
  
- `list_passwords`: Lists all stored passwords. It reads each line from the password file, splits it into service, username, and encrypted password, decrypts the password, and prints the service and username.

##### `__main__` block:
This block contains the main logic of the password manager application. It creates an instance of the `PasswordManager` class and provides a menu-driven interface for users to interact with the password manager.

#### Example Usage:
```python
password_manager = PasswordManager()
password_manager.save_password("Facebook", "user123", "password123")
password = password_manager.get_password("Facebook", "user123")
print(password)  # Output: password123
```

This detailed documentation provides a comprehensive understanding of the project, including the purpose of libraries used, the functionality of each function, and how encryption and decryption are implemented using the `Fernet` tool from the `cryptography` library.
