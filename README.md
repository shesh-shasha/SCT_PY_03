# SCT_PY_03
STRENGTH OF A PASSWORD
import re

def check_password_strength(password):
    """
    Checks the strength of a password based on:
    - Length
    - Uppercase letters
    - Lowercase letters
    - Digits
    - Special characters
    """

    length_error = len(password) < 8
    uppercase_error = not re.search(r"[A-Z]", password)
    lowercase_error = not re.search(r"[a-z]", password)
    digit_error = not re.search(r"\d", password)
    special_char_error = not re.search(r"[!@#$%^&*(),.?\":{}|<>]", password)

    # Count how many conditions are met
    passed_checks = 5 - sum([length_error, uppercase_error, lowercase_error, digit_error, special_char_error])

    # Determine strength based on checks passed
    if passed_checks == 5:
        strength = "Strong"
    elif passed_checks >= 3:
        strength = "Moderate"
    else:
        strength = "Weak"

    return strength

# ----------- INPUT & OUTPUT ------------

if __name__ == "__main__":
    user_password = input("Enter a password to check its strength: ")
    result = check_password_strength(user_password)
    print(f"Password strength: {result}")
