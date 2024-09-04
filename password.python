import tkinter as tk
import random
import string


class PasswordGenerator:
    def __init__(self, master):
        self.master = master
        master.title("Advanced Password Generator")

        # Password length
        self.length_label = tk.Label(master, text="Password Length:")
        self.length_label.pack()
        self.length_entry = tk.Entry(master)
        self.length_entry.pack()

        # Character sets
        self.has_letters_var = tk.IntVar()
        self.has_numbers_var = tk.IntVar()
        self.has_symbols_var = tk.IntVar()
        self.has_uppercase_var = tk.IntVar()
        self.has_lowercase_var = tk.IntVar()

        self.has_letters_checkbox = tk.Checkbutton(master, text="Include Letters", variable=self.has_letters_var)
        self.has_letters_checkbox.pack()
        self.has_numbers_checkbox = tk.Checkbutton(master, text="Include Numbers", variable=self.has_numbers_var)
        self.has_numbers_checkbox.pack()
        self.has_symbols_checkbox = tk.Checkbutton(master, text="Include Symbols", variable=self.has_symbols_var)
        self.has_symbols_checkbox.pack()
        self.has_uppercase_checkbox = tk.Checkbutton(master, text="Include Uppercase Letters", variable=self.has_uppercase_var)
        self.has_uppercase_checkbox.pack()
        self.has_lowercase_checkbox = tk.Checkbutton(master, text="Include Lowercase Letters", variable=self.has_lowercase_var)
        self.has_lowercase_checkbox.pack()

        # Excluded characters
        self.excluded_characters_label = tk.Label(master, text="Excluded Characters:")
        self.excluded_characters_label.pack()
        self.excluded_characters_entry = tk.Entry(master)
        self.excluded_characters_entry.pack()

        # Generate password button
        self.generate_button = tk.Button(master, text="Generate Password", command=self.generate_password)
        self.generate_button.pack()

        # Password display
        self.password_label = tk.Label(master, text="Generated Password:")
        self.password_label.pack()
        self.password_entry = tk.Entry(master)
        self.password_entry.pack()

        # Copy to clipboard button
        self.copy_button = tk.Button(master, text="Copy to Clipboard", command=self.copy_to_clipboard)
        self.copy_button.pack()

    def generate_password(self):
        length = int(self.length_entry.get())
        has_letters = self.has_letters_var.get() == 1
        has_numbers = self.has_numbers_var.get() == 1
        has_symbols = self.has_symbols_var.get() == 1
        has_uppercase = self.has_uppercase_var.get() == 1
        has_lowercase = self.has_lowercase_var.get() == 1

        characters = ''
        if has_letters:
            characters += string.ascii_letters
        if has_numbers:
            characters += string.digits
        if has_symbols:
            characters += string.punctuation
        if has_uppercase:
            characters += string.ascii_uppercase
        if has_lowercase:
            characters += string.ascii_lowercase

        excluded_characters = self.excluded_characters_entry.get()
        for char in excluded_characters:
            characters = characters.replace(char, '')

        password = ''
        for i in range(length):
            password += random.choice(characters)

        self.password_entry.delete(0, tk.END)
        self.password_entry.insert(0, password)

    def copy_to_clipboard(self):
        password = self.password_entry.get()
        pyperclip.copy(password)

root = tk.Tk()
my_gui = PasswordGenerator(root)
root.mainloop()
