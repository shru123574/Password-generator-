# Password-generator-
import random
import string

def generate_password(length, include_digits=True, include_special_chars=True):
    """
    Generates a random password based on specified criteria.

    Args:
        length (int): The desired length of the password.
        include_digits (bool): Whether to include digits (0-9).
        include_special_chars (bool): Whether to include special characters.

    Returns:
        str: The generated password.
    """
    characters = string.ascii_letters  # Start with letters (uppercase and lowercase)

    if include_digits:
        characters += string.digits
    if include_special_chars:
        characters += string.punctuation

    if length <= 0:
        return "Password length must be greater than 0."
    if not characters:
        return "No character types selected for password generation."

    password = ''.join(random.choice(characters) for _ in range(length))
    return password

if __name__ == "__main__":
    try:
        desired_length = int(input("Enter desired password length: "))
        include_nums = input("Include numbers? (y/n): ").lower() == 'y'
        include_specials = input("Include special characters? (y/n): ").lower() == 'y'

        generated_pwd = generate_password(desired_length, include_nums, include_specials)
        print(f"Generated Password: {generated_pwd}")

    except ValueError:
        print("Invalid input. Please enter a valid number for length.")
