# INTERNPEDIA
# tast 3, password generator
import secrets
import string
import pyperclip

def generate_password(length, complexity):
    characters = string.ascii_lowercase
    if complexity >= 1:
        characters += string.ascii_uppercase
    if complexity >= 2:
        characters += string.digits
    if complexity >= 3:
        characters += string.punctuation

    password = ''.join(secrets.choice(characters) for _ in range(length))
    return password

def main():
    print("Password Generator")
    while True:
        print("\nChoose an option:")
        print("1. pls Generate password")
        print("2. Exit")

        choice = input("Enter your choice (1-2): ")

        if choice == "2":
            print(" Thank You Goodbye!")
            break
        elif choice == "1":
            length = int(input("Enter password length: "))
            complexity = int(input("Enter password complexity (0-3): "))

            if length < 8:
                print("Password length should be at least 8 characters.")
                continue
            if complexity < 0 or complexity > 3:
                print("Password complexity should be between 0 and 3.")
                continue

            password = generate_password(length, complexity)
            print(f"Generated Password: {password}")
            copy_choice = input("Copy to clipboard? (y/n): ")
            if copy_choice.lower() == 'y':
                pyperclip.copy(password)
                print("Password copied to clipboard.")
        else:
            print("Invalid choice, so Please choose a valid option.")
if __name__ == "__main__":
    main()
