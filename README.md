# ElevateLabsDay3
Task 3 : Perform a Basic Vulnerability Scan on Your PC.

# Tenable Nessus Vulnerability Scan Report

**Target Host:** `192.168.1.44`
**Operating System:** `Windows 11`
**Scan Duration:** \~8 minutes
**Tool Used:** Tenable Nessus Essentials

---

## 1. Summary of Detected Vulnerabilities

| Severity | Vulnerability             | Description                              | Count | Family            |
| -------- | ------------------------- | ---------------------------------------- | ----- | ----------------- |
| Medium   | SMB Signing Not Required  | Allows MITM attacks on SMB traffic       | 1     | Misc.             |
| Medium   | SSL (Multiple Issues)     | Weak encryption and deprecated protocols | 4     | General           |
| Info     | SMB (Multiple Issues)     | General SMB configuration issues         | 6     | Windows           |
| Info     | HTTP (Multiple Issues)    | Web server-related findings              | 2     | Web Servers       |
| Info     | Microsoft Windows Issues  | OS configuration findings                | 2     | Windows           |
| Info     | TLS (Multiple Issues)     | Insecure TLS protocol support            | 2     | Service Detection |
| Info     | Netstat Portscanner (SSH) | Detected 39 open ports                   | 39    | Port Scanners     |
| Info     | DCE Services Enumeration  | RPC service detection                    | 8     | Windows           |
| Info     | Service Detection         | General service enumeration              | 3     | Service Detection |

---

## 2. Key Issues and Suggested Fixes

### Medium Severity

* **SMB Signing Not Required**

  * **Risk:** Potential MITM attacks.
  * **Fix:** Enforce SMB signing via Group Policy or registry. Disable SMBv1 if unnecessary.

* **SSL (Multiple Issues)**

  * **Risk:** Use of deprecated SSL protocols or weak ciphers.
  * **Fix:** Disable SSLv2/SSLv3, and TLS 1.0/1.1. Use TLS 1.2 or 1.3 with strong cipher suites.

### Informational Issues

* **Netstat Portscanner (SSH)**

  * **Risk:** Multiple open ports may expose services to attackers.
  * **Fix:** Disable unused services or block access via firewall.

* **Service Detection / TLS / OS Enumeration**

  * **Risk:** Reveals software versions and OS details.
  * **Fix:** Limit exposed services, obfuscate banners, and apply strict access rules.

---

## 3. Most Critical Vulnerabilities

| Severity | Vulnerability            | Fix Summary                                |
| -------- | ------------------------ | ------------------------------------------ |
| Medium   | SMB Signing Not Required | Enforce SMB signing; disable SMBv1         |
| Medium   | SSL (Multiple Issues)    | Enforce TLS 1.2/1.3; remove weak protocols |
| Info     | Port Scanner (SSH)       | Close or firewall unnecessary ports        |
| Info     | TLS (Multiple Issues)    | Disable legacy TLS versions                |
| Info     | Service Detection        | Harden banners; limit visible services     |

---

## 4. Screenshots Captured

* **Screenshot 1:** Overview of 25 vulnerabilities on host `192.168.1.44`
* 
  ![image](https://github.com/user-attachments/assets/b79bdcda-1f5c-4f67-ae4c-ad13b61dede1)


* **Screenshot 2:** Extended list including port scan and TLS issues

![image](https://github.com/user-attachments/assets/44854238-0359-440d-ad7a-a101de9c94b1)


* **Screenshot 3:** Additional INFO findings like OS/service enumeration

![image](https://github.com/user-attachments/assets/65696ab0-7758-4b24-abdd-695b0780043c)

---

## 5. Conclusion

This Nessus Essentials scan found no high or critical vulnerabilities. However, multiple medium and informational issues were identified. Remediation should prioritize enforcing SMB and TLS best practices, minimizing exposed services, and reducing leaked metadata. These actions will strengthen the overall security posture of the system.

---


