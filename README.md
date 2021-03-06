# Oneline Hangman
Hangman, written in one line of code.

## To Play
1. Clone this repository
2. Run it in Python: `python3 hangman.py`
3. When prompted, guess a letter by entering it in the command prompt.

Note that for Windows, the `requests` library is a dependency, but for Mac and Linux there are no external dependencies. This is because the word bank for the game is the `usr/share/dict/words` file that is present on Unix systems, and for Windows the program uses `requests` to get an online version of the file ([present here](https://users.cs.duke.edu/~ola/ap/linuxwords)).

## About
This program makes use of lambda functions in Python to condense a full Hangman game to one line.

Instead of while loops, functions such as `get_guess` were called recursively. Normally this is difficult with unnamed lambdas, but this snippet allows us to do so:
```
(lambda f: lambda *args: f(f, *args))
```
This acts as a pseudo-decorator for lambdas, allowing them to access themselves (the `self` argument in the code) as their first parameter. This lets the functions pass themselves around and call themselves recursively. [See this Wikipedia page on Y-combinators](https://en.wikipedia.org/wiki/Fixed-point_combinator#Y_combinator).

Program state is initiated in the arguments for the largest lambda, and is then passed through all of the functions.

Other necessary techniques include list comprehensions, ternary operators, and `__import__()` for inline imports.

Techniques that were not used, but would make the program easier to write:
- Semicolons
- Lists of function calls that essentially act as multiple lines (like semicolons)
- `exec()`
