Authentication Checklist

[+] Focuses on common vulnerabilities related to authentication mechanisms.

### **Terminology**

- **Identification is** a statement about who you are. Depending on the situation, it can be: name, email address, account number, etc.
- **Authentication** is the provision of evidence that you are actually the one who is identified.
- **Authorization** – check that you are allowed access to the requested resource.
- **Access Tokens**

**For example**: when trying to get into a closed club you *identify* (a question your name and surname),*Authenticate*(a question to show the passport and check the photo) and *Authorized*(they will check that the surname is on the guest list) before let it inside.

Similarly, these terms are used in computer systems, where traditionally under *Identification* understand the receipt of your account (identity) by username or email; under *Authentication* – check that you know the password from this account, and under *Authorization* – checking your role in the system and the decision to provide access to the requested page or resource.
  
---
### 1. CAPTCHA Bypass via `X-Forwarded-For`
- **Description:** Attackers bypass CAPTCHA using proxy headers like `X-Forwarded-For`.
- **Steps to Test:**
  1. Submit multiple CAPTCHA-protected requests from different IP addresses using a proxy.
  2. Check if the server tracks the real client IP or relies on `X-Forwarded-For`.
- **Mitigation:** Validate the client IP on the backend and enforce CAPTCHA per session.

---

### 2. Lack of Password Confirmation
- **Description:** Sensitive actions like password resets are completed without confirming the old password.
- **Steps to Test:**
  1. Attempt to reset the password without inputting the current one.
  2. Check if the system allows the action.
- **Mitigation:** Always require the current password for sensitive actions.

---

### 3. Lack of Verification Email
- **Description:** New accounts or critical email updates proceed without email verification.
- **Steps to Test:**
  1. Register an account or change the email address.
  2. Verify if the system sends a confirmation email.
- **Mitigation:** Implement mandatory email verification steps for registration and updates.

---

### 4. No Rate Limiting on Forms
- **Description:** Forms can be submitted repeatedly without restrictions, allowing brute force attacks.
- **Steps to Test:**
  1. Submit the form multiple times with automated tools.
  2. Observe if there are any rate limits or restrictions.
- **Mitigation:** Apply rate-limiting controls on forms.

---

### 5. No Rate Limiting or CAPTCHA on Login Page
- **Description:** Login forms allow brute force attacks due to the absence of rate limiting or CAPTCHA.
- **Steps to Test:**
  1. Attempt multiple login attempts with different credentials.
  2. Check for rate limits or CAPTCHA challenges.
- **Mitigation:** Implement rate-limiting and CAPTCHA mechanisms on the login page.

---

### 6. Username/Email Address Enumeration
- **Description:** Error messages reveal if a username or email exists in the system.
- **Steps to Test:**
  1. Attempt to register or reset a password with an existing and non-existing username/email.
  2. Observe if error messages vary (e.g., "user not found").
- **Mitigation:** Use generic error messages like "Invalid credentials" for all cases.

---

### 7. Weak Password Policy
- **Description:** The application accepts passwords that do not meet strong security criteria.
- **Steps to Test:**
  1. Create accounts with weak passwords (e.g., "123456").
  2. Check if password complexity requirements are enforced.
- **Mitigation:** Enforce strong password policies, including length and complexity rules.

---

### 8. Weak Registration Implementation over HTTP
- **Description:** User registration data is transmitted over unencrypted HTTP.
- **Steps to Test:**
  1. Monitor network traffic during registration.
  2. Check if sensitive data is transmitted in plaintext.
- **Mitigation:** Use HTTPS for all data transmission.

---

### 9. Broken Authentication Session Token
- **Description:** Session tokens are exposed, predictable, or insecurely managed.
- **Steps to Test:**
  1. Analyze session tokens for predictable patterns.
  2. Check for token leakage in URLs, headers, or logs.
- **Mitigation:** Use secure, randomly generated tokens and protect them from exposure.

---

### 10. Username Enumeration via Response Timing
- **Description:** Timing differences in responses reveal valid usernames.
- **Steps to Test:**
  1. Send login requests with valid and invalid usernames.
  2. Measure response time for each case.
- **Mitigation:** Standardize response times for valid and invalid credentials.

---

  
## Additional Resources
- [OWASP Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
- [NIST Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)