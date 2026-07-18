# 🔒 AI Security Scanner for Python

A command-line tool that uses Google's Gemini AI to scan Python files for security vulnerabilities — identifying issues like SQL injection, hardcoded credentials, weak cryptography, and command injection, then explaining *why* they're risky and how to fix them.

## 📋 Overview

This project connects to the **Gemini API** and turns it into a focused security analysis engine using prompt engineering. Instead of chatting generally, Gemini is instructed to act as a security expert and return structured, consistent vulnerability reports for any Python file you give it.

For each issue found, the scanner reports:
1. **Vulnerability Type**
2. **Why it's vulnerable**
3. **Impact**
4. **Secure code fix**

## ✨ Features

- 🔍 Scans real Python files from disk for security vulnerabilities
- 🤖 Powered by Google Gemini (`gemini-3.5-flash`)
- 📝 Structured, easy-to-read vulnerability reports
- 🔐 Secure API key handling via `.env` (never hardcoded or committed)
- ⚡ Simple CLI usage — just point it at a file

## 🛠️ Tech Stack

- **Python 3.13**
- **Google Gemini API** (`google-genai`)
- **python-dotenv** for environment variable management

## 📦 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/sarafay2003/ai-security-scanner.git
   cd ai-security-scanner
   ```

2. **Create and activate a virtual environment**
   ```bash
   python -m venv venv
   # Windows
   venv\Scripts\activate
   # macOS/Linux
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install google-genai python-dotenv
   ```

4. **Set up your API key**

   Create a `.env` file in the project root (this file is git-ignored and should never be committed):
   ```
   GOOGLE_API_KEY=your_gemini_api_key_here
   ```

   Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).

## 🚀 Usage

Run the scanner against any Python file:

```bash
python scanner.py <file_path>
```

**Example:**
```bash
python scanner.py vulnerable.py
```

**Example output:**
```
### Issue 1: Use of Hardcoded Credentials
1. **Vulnerability Type:** Hardcoded Credentials (CWE-798)
2. **Why it is vulnerable:** The database password and API secret are stored 
   in plaintext directly within the application source code.
3. **Impact:** Anyone who gains access to the source code repository can 
   compromise both the database and the associated API service.
4. **Secure code fix:** Load credentials from secure environment variables.
```

## 🔎 Vulnerability Types Detected

- SQL Injection
- OS Command Injection
- Hardcoded Credentials / Secrets
- Weak Cryptographic Algorithms (e.g., MD5)
- Insecure Deserialization
- Path Traversal
- Unvalidated/Unsanitized Input

## 📁 Project Structure

```
ai-security-scanner/
├── scanner.py          # Main CLI script
├── vulnerable.py        # Sample file with intentional vulnerabilities (for testing)
├── .env                 # API key (not committed — see .gitignore)
├── .gitignore
└── README.md
```

## 🗺️ Roadmap

- [ ] Build a web UI (Flask/FastAPI) so the scanner can be used without running scripts manually
- [ ] Add batch scanning for entire directories/projects
- [ ] Export scan reports to PDF/HTML
- [ ] Add support for other languages beyond Python

## ⚠️ Disclaimer

This tool uses an LLM for analysis and is intended as a **first-pass educational aid**, not a replacement for established static analysis tools (e.g., Bandit, Semgrep) or professional security audits.

## 👤 Author

**Syed Rafay**
Built as part of a hands-on learning project via [NextWork](https://nextwork.ai)

## 📄 License

This project is licensed under the MIT License.
