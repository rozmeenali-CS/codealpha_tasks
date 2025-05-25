import random

# 5 predefined words
word_list = ["apple", "robot", "plane", "tiger", "chair"]

# Randomly choose a word from the list
secret_word = random.choice(word_list)
guessed_letters = []
incorrect_guesses = 0
max_guesses = 6

# Create a display with underscores
display_word = ["_" for _ in secret_word]

print("Welcome to Hangman!")
print("Guess the word, one letter at a time.")

# Main game loop
while incorrect_guesses < max_guesses and "_" in display_word:
    print("\nWord: " + " ".join(display_word))
    guess = input("Enter a letter: ").lower()

    if guess in guessed_letters:
        print("You already guessed that letter.")
    elif guess in secret_word:
        print("Correct guess!")
        for index, letter in enumerate(secret_word):
            if letter == guess:
                display_word[index] = guess
        guessed_letters.append(guess)
    else:
        print("Wrong guess!")
        incorrect_guesses += 1
        guessed_letters.append(guess)
        print(f"Incorrect guesses: {incorrect_guesses}/{max_guesses}")

# Game result
if "_" not in display_word:
    print("\nCongratulations! You guessed the word:", secret_word)
else:
    print("\nGame over! The word was:", secret_word)
