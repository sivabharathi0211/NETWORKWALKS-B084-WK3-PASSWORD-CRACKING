# NETWORKWALKS-B084-WK3-PASSWORD-CRACKING

# 🔐 Password Cracking with John the Ripper and NW Tools

A hands-on cybersecurity lab demonstrating offline dictionary attacks against password-protected PDF documents using **John the Ripper**, **pdf2john**, and the **NW Hash Calculator** by Networkwalks.

This project explores how weak PDF passwords can be recovered through dictionary attacks and highlights the importance of strong password practices and secure document encryption.


## 📌 Project Overview

Password-protected PDF documents use encryption to prevent unauthorized access. However, weak or commonly used passwords can be vulnerable to offline dictionary attacks.

This lab demonstrates two approaches to recovering weak PDF passwords:

- Extracting PDF password hashes using NW Hash Calculator.
- Extracting hashes using `pdf2john` in Kali Linux.
- Performing dictionary attacks using John the Ripper.
- Using the `rockyou.txt` wordlist to test common passwords.
- Displaying recovered passwords.
- Understanding password security weaknesses.

## 🛠️ Tools and Technologies

| Tool | Purpose |
|---|---|
| Kali Linux | Testing environment |
| John the Ripper | Offline password cracking |
| pdf2john | Extracting password hashes from PDFs |
| NW Hash Calculator | Browser-based PDF hash extraction and password testing |
| rockyou.txt | Common-password dictionary wordlist |
| Terminal | Executing commands |

## ⚙️ Prerequisites

- Kali Linux or a compatible Linux distribution.
- John the Ripper installed.
- pdf2john utility available.
- rockyou.txt and JTR_default_password wordlist.
- Password-protected PDF lab files.
- Internet browser for NW Hash Calculator.


## 🚀 Lab Implementation

This project demonstrates two methods of PDF password recovery.

### 🔹 Method 1: Password Cracking Using NW Hash Calculator

The NW Hash Calculator is a browser-based tool provided by Networkwalks.

**Steps:**

1. Open the NW Hash Calculator.
2. Navigate to the PDF section.
3. Upload the password-protected PDF.
4. Allow the tool to identify the encrypted document.
5. Copy the generated PDF hash.
6. Select the built-in password list or upload a custom wordlist.
7. Execute the dictionary attack.
8. Check whether the password is successfully recovered.

**PDF 1 Hash Extraction**
<img width="898" height="540" alt="Screenshot 2026-11-20 135221" src="https://github.com/user-attachments/assets/7da6b9cb-2cd2-4cba-bee0-6716d06dc2fa" />



**PDF 1 Password Recovery**
<img width="1014" height="633" alt="Screenshot 2026-11-20 132953" src="https://github.com/user-attachments/assets/63ff3535-afd2-441f-acc8-8f6adc6a54ee" />



**PDF 1**
<img width="400" height="505" alt="Screenshot 2026-11-20 135000" src="https://github.com/user-attachments/assets/b52141f3-45c5-4932-92ad-fbe47dcc2c32" />


### 🔹 Method 2: Password Cracking Using John the Ripper

This method uses Kali Linux terminal commands to extract and crack PDF password hashes.

**Step 1: Navigate to the Lab Directory**

```bash
cd ~/Downloads
```

**Step 2: Extract the PDF Hash**

```bash
pdf2john "My Locked PDF1.pdf" > "pdf hash1.txt"
```

**Step 3: View the Extracted Hash**

```bash
cat "pdf hash1.txt"
```

The extracted output contains a PDF hash beginning with `$pdf$`.

**Step 4: Perform a Dictionary Attack**

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt "pdf hash1.txt"
```

John the Ripper compares password candidates from the wordlist against the extracted hash.

**Step 5: Display the Recovered Password**

```bash
john --show --format=PDF "pdf hash1.txt"
```


**PDF 1 Password Cracking in Kali Linux**
<img width="1366" height="643" alt="pdf 1 JTR" src="https://github.com/user-attachments/assets/c17cc641-1c5b-424d-b49b-43d8815a5cff" />


## 📂 Repeating the Process for Multiple PDF Files

The same procedure was performed on three different password-protected PDF lab files.

### PDF 2 – Password Recovery

**Commands:**

```bash
pdf2john "My Locked PDF2.pdf" > "pdf hash2.txt"

john --wordlist=/usr/share/wordlists/rockyou.txt "pdf hash2.txt"

john --show --format=PDF "pdf hash2.txt"
```

**PDF 2 Hash Extraction**
<img width="930" height="627" alt="1000162657" src="https://github.com/user-attachments/assets/aa84c5b9-c45e-4c3f-a4de-b3487910fa5b" />



**PDF 2 Password Recovery Using NW Tools**

<img width="923" height="620" alt="1000162658" src="https://github.com/user-attachments/assets/47b1b14f-edf9-488a-aaa7-35fbc98064c2" />



**PDF 2 Password Cracking Using John**
<img width="1366" height="643" alt="1000162673" src="https://github.com/user-attachments/assets/f107aa37-43d1-429b-bb2d-67b40bdfda5c" />


**PDF 2**
<img width="460" height="569" alt="Screenshot 2026-11-16 221441" src="https://github.com/user-attachments/assets/f0aecee0-ad89-4f31-ad4f-5ae22778c64c" />


### PDF 3 – Password Recovery

**Commands:**

```bash
pdf2john "My Locked PDF3.pdf" > "pdf hash3.txt"

john --wordlist=/usr/share/wordlists/rockyou.txt "pdf hash3.txt"

john --show --format=PDF "pdf hash3.txt"
```

**PDF 3 Hash Extraction**

<img width="939" height="628" alt="1000162664" src="https://github.com/user-attachments/assets/6bfb3374-60ff-4e51-b6c2-3ea70f3daeb2" />


**PDF 3 Password Recovery Using NW Tools**

<img width="1013" height="636" alt="1000162665" src="https://github.com/user-attachments/assets/17d48015-1557-40f1-9428-da1134125c08" />


**PDF 3 Password Cracking Using John**

<img width="1366" height="643" alt="1000162675" src="https://github.com/user-attachments/assets/a59a54e9-5f85-4277-a531-93c12adc46e0" />

**PDF3**

<img width="813" height="574" alt="Screenshot 2026-11-16 222212" src="https://github.com/user-attachments/assets/797d73f6-b22d-40cc-b519-23fed8d65a27" />


## 📊 Results and Observations

The lab successfully demonstrated password recovery against three encrypted PDF files using dictionary-based password testing.

| Lab File | Hash Extraction | Cracking Method | Result |
|---|---|---|---|
| PDF 1 | NW Hash Calculator / pdf2john | JTR_default_password | ✅ Recovered |
| PDF 2 | NW Hash Calculator / pdf2john | Built-in list | ✅ Recovered |
| PDF 3 | NW Hash Calculator / pdf2john | Built-in list | ✅ Recovered |

**Observation:** All three lab PDF passwords were recovered because the passwords were present in commonly used password dictionaries.

Actual cracking time depends on password strength, PDF encryption settings, hash type, hardware, and the wordlist used.

## 🔍 Key Learnings

- **PDF Hash Extraction:** Learned how to extract password hashes from encrypted PDF documents.
- **Dictionary Attacks:** Understood how password-cracking tools test common password combinations.
- **John the Ripper:** Gained practical experience with offline password recovery using Kali Linux.
- **NW Hash Calculator:** Explored browser-based PDF hash extraction and password testing.
- **Password Security:** Understood why weak and predictable passwords are vulnerable.
- **Offline Cracking:** Learned why extracted hashes can be tested without interacting with the original document.

## 🛡️ Security Recommendations

To protect sensitive PDF documents:

1. Use long and randomly generated passwords (preferably 16+ characters).
2. Avoid common words, names, dates, and predictable patterns.
3. Never reuse passwords across different documents or accounts.
4. Use a password manager to generate and store secure passwords.
5. Prefer modern PDF encryption configurations, such as AES-256, where supported.
6. Apply additional access controls when storing sensitive documents.


## 📚 References

- [Kali Linux – John the Ripper](https://www.kali.org/tools/john/)
- [Networkwalks](https://networkwalks.com)

## 🎯 Conclusion

This hands-on lab provided practical experience in extracting PDF password hashes and performing offline dictionary attacks using John the Ripper and NW Hash Calculator.

It demonstrated how weak passwords can compromise encrypted documents and reinforced the importance of strong passwords and secure encryption practices.

---
## Author

Siva Bharathi R | Cybersecurity Student

**🔐 Project Category:** Cybersecurity | Password Cracking | Ethical Hacking  
**💻 Environment:** Kali Linux  
**🧪 Attack Technique:** Offline Dictionary Attack  
**📖 Purpose:** Educational and Authorized Security Testing
