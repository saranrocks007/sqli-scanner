# SQL Injection Scanner
A lightweight Python SQL Injection detection tool designed for bug bounty hunters, penetration testers, and cybersecurity professionals.

This scanner tests web parameters for potential SQL Injection vulnerabilities using multiple techniques:

Classic SQL injection payloads
Error-based detection
UNION-based probing
Time-based blind injection

⚠️ Legal Disclaimer

This tool is for authorized security testing only.

Only use this tool on:

Systems you own, or
Targets where you have explicit written permission (e.g., bug bounty programs).

Unauthorized scanning may be illegal.

Features
Automated SQL Injection testing
Supports GET and POST parameters
Error-based detection
Time-based blind detection
Cookie/session authentication support
Multi-thread scanning
Adjustable scan depth (level 1–3)
Detailed scan report
Debug mode for troubleshooting sessions
Requirements

The scanner is written in Python 3 and requires the following package:

Preinstalled / Required Tools
Python 3.7+
pip
Internet access
Python Libraries
requests

Install dependencies:

pip install requests
Installation

Clone the repository from GitHub:

git clone https://github.com/saranrocks007/sqli-scanner.git

Go into the project directory:

cd sqli-scanner

Install dependencies:

pip install -r requirements.txt
Basic Usage

Run the scanner with a target URL containing parameters:

python sqli_scanner.py -u "https://target.com/page?id=1"
Examples
Basic Scan
python sqli_scanner.py -u "https://target.com/page?id=1"
Medium Depth Scan
python sqli_scanner.py -u "https://target.com/page?id=1" --level 2
Full Scan (includes time-based attacks)
python sqli_scanner.py -u "https://target.com/page?id=1" --level 3
POST Request Testing
python sqli_scanner.py -u "https://target.com/login" --method POST --data "user=admin&pass=test"
Authenticated Scan Using Cookies
python sqli_scanner.py -u "https://target.com/profile?id=1" --cookies "session=abc123"
Save Scan Report
python sqli_scanner.py -u "https://target.com/page?id=1" --out report.txt
Scan Levels
Level	Description
1	Basic payloads (fast)
2	Error-based and UNION injection tests
3	Time-based blind injection tests
Debug Mode

If the scanner returns no results, enable debug mode:

python sqli_scanner.py -u "https://target.com/page?id=1" --debug

Debug mode prints the baseline HTTP response, which helps identify:

Session expiration
Login redirects
Cookie issues
Getting Session Cookies

Some applications require authentication.

Steps:

Log in to the target website.
Open browser DevTools (F12) in Google Chrome.
Go to Application → Cookies.
Copy your session cookie.
Run the scanner:
--cookies "session=YOUR_COOKIE_VALUE"
Output Example
[VULN] DB error (MySQL) | param='id' | payload: ' OR 1=1--

The scanner will report:

Vulnerable parameter
Payload used
Database type
Evidence
Reporting

Reports can be saved using:

--out report.txt
Contribution

Contributions are welcome.

You can help by:

Adding new payloads
Improving detection logic
Fixing bugs
Improving documentation
Author

Cybersecurity Research Tool
Built for bug bounty hunters and penetration testers.
