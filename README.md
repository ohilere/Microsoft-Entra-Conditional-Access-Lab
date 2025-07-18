# Microsoft-Entra-Conditional-Access-Lab
# Azure Conditional Access Lab

## Overview
This lab demonstrates how to build, test, and enforce Conditional Access policies in Microsoft Entra ID (Azure AD).

---

## Objectives
- Create and test Conditional Access policies
- Configure location-based access control
- Block legacy authentication
- Enforce MFA for external users
- Move policies from Report-only to Enforced mode

---

## Architecture Summary

- **Microsoft Entra** evaluates each sign-in request.
- If user is **off trusted network** or on **non-compliant device** → MFA is required.
- If sign-in uses **legacy protocols (e.g., IMAP, POP)** → Block access.
- **Break-glass accounts** are excluded from all policies.
---

## Architecture
![Architecture Diagram](https://imgur.com/ppukOmR.png)

---

## Steps

### 1. Setup Environment
- Ensure tenant has Entra ID P1 or P2 license
- Enable MFA and register test users
- Create two groups: CA‑Included (users affected) and CA‑Excluded (globaladmins). Add user accounts accordingly.


#### Groups create
![Groups](https://imgur.com/SEDMudd.png)


### 2. Create Named Locations
- Tag trusted IPs under Entra ID → Protection → Named Locations

#### Setting up the named location
![Policy](https://imgur.com/DGm6Ojw.png)

### 3. Create Conditional Access Policies
- Require MFA for external/untrusted users
- Block legacy protocols (IMAP, POP)

#### Conditional Access Policies
![Policy](https://imgur.com/cV8ezwm.png)

### 4. Test with 'What If' Tool
- Validate policy behavior before enforcement

### 5. Move to Enforcement
- Switch policy mode from Report-only to On

### 6. Test Cases

| Scenario                                    | Expected Outcome | Status |
|---------------------------------------------|------------------|--------|
| User on compliant device + trusted IP       | No MFA           | ✅      |
| User on non-compliant device                | MFA Required     | ✅      |
| External user with IMAP email client        | Blocked          | ✅      |
| Admin (break-glass) login                   | No policy applied| ✅      |

### 7. Use sign-in logs to monitor policy enforcement
![Policy](https://imgur.com/a9Y37fb.png)
![Policy](https://imgur.com/lEzLw7t.png)
---



## Backup
- Exported JSON backup of Conditional Access policies

- Sample test results
- Policy screenshot examples

---

## Author
**[Your Name]** – Cloud Administrator & IAM Enthusiast  
🔗 [LinkedIn Profile]  
