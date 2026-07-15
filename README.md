# Password Checker

A comprehensive Python tool that evaluates password security through strength analysis and breach detection.

## Features

- 🔐 **Strength Analysis** — Checks length, uppercase, lowercase, numbers, and symbols
- 📊 **Score System** — Rates passwords from 0-6 with clear feedback
- 🛡️ **Breach Detection** — Checks HaveIBeenPwned API for leaked passwords
- 🎯 **Privacy First** — Uses k-anonymity (only sends first 5 chars of hash)
- 💻 **Command-Line Support** — Quick checks without interactive prompts
- 📝 **Detailed Feedback** — Explains exactly what's missing or working
- 🎨 **Clean Output** — Easy-to-read results with emoji indicators

## How It Works

### Strength Analysis

The tool evaluates your password against five security criteria:

| Criteria | Points | Example |
|----------|--------|---------|
| Length (12+ characters) | 2 | `"HelloWorld123!"` |
| Length (8-11 characters) | 1 | `"Hello123!"` |
| Uppercase letters | 1 | `"Password"` |
| Lowercase letters | 1 | `"password"` |
| Numbers | 1 | `"123"` |
| Symbols | 1 | `"!@#"` |

**Score Interpretation:**

| Score | Rating | Meaning |
|-------|--------|---------|
| 5-6 | 🟢 GREAT | Excellent password — very secure |
| 4 | 🟢 GOOD | Solid password — safe to use |
| 3 | 🔴 DECENT | Okay — could be improved |
| 0-2 | 🔴 WEAK | Avoid — easily cracked |

### Breach Detection

The tool uses the HaveIBeenPwned API to check if your password has been leaked:

1. **Hash the password** — Converts your password to a SHA-1 hash
2. **Split the hash** — Sends only the first 5 characters (privacy protection)
3. **Query the API** — Receives all hashes that start with those 5 characters
4. **Check for match** — If your full hash is in the response, your password has been leaked

**Why this is secure:** The API never sees your full password or full hash.

## Installation

### Prerequisites

- Python 3.6 or higher
- pip (Python package manager)

### Install Dependencies

```bash
pip install requests
