---
title: "USN-522-1: OpenSSL vulnerabilities"
date: 2007-09-28
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-09-28
Referenced CVEs:
CVE-2007-3108, CVE-2007-5135


Description:
 ===========================================================  Ubuntu Security Notice USN-522-1         September 29, 2007 openssl vulnerabilities CVE-2007-3108, CVE-2007-5135 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libssl0.9.8                     0.9.8a-7ubuntu0.4  Ubuntu 6.10:   libssl0.9.8                     0.9.8b-2ubuntu2.1  Ubuntu 7.04:   libssl0.9.8                     0.9.8c-4ubuntu0.1  After a standard system upgrade you need to reboot your computer to affect the necessary changes.  Details follow:  It was discovered that OpenSSL did not correctly perform Montgomery multiplications.  Local attackers might be able to reconstruct RSA private keys by examining another user's OpenSSL processes. (CVE-2007-3108)  Moritz Jodeit discovered that OpenSSL's SSL_get_shared_ciphers function did not correctly check the size of the buffer it was writing to. A remote attacker could exploit this to write one NULL byte past the end of an application's cipher list buffer, possibly leading to arbitrary code execution or a denial of service. (CVE-2007-5135) 





[More...](http://www.ubuntu.com/usn/usn-522-1)

---

