---
title: "USN-620-1: OpenSSL vulnerabilities"
date: 2008-06-26
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-06-26
Referenced CVEs: 
CVE-2008-0891, CVE-2008-1672


Description: 
 ===========================================================  Ubuntu Security Notice USN-620-1              June 26, 2008 openssl vulnerabilities CVE-2008-0891, CVE-2008-1672 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   libssl0.9.8                     0.9.8g-4ubuntu3.3  After a standard system upgrade you need to reboot your computer to effect the necessary changes.  Details follow:  It was discovered that OpenSSL was vulnerable to a double-free when using TLS server extensions. A remote attacker could send a crafted packet and cause a denial of service via application crash in applications linked against OpenSSL. Ubuntu 8.04 LTS does not compile TLS server extensions by default. (CVE-2008-0891)  It was discovered that OpenSSL could dereference a NULL pointer. If a user or automated system were tricked into connecting to a malicious server with particular cipher suites, a remote attacker could cause a denial of service via application crash. (CVE-2008-1672) 





[More...](http://www.ubuntu.com/usn/usn-620-1)

---

