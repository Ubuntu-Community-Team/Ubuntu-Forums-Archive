---
title: "USN-646-1: rdesktop vulnerabilities"
date: 2008-09-18
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-09-18
Referenced CVEs: 
CVE-2008-1801, CVE-2008-1802, CVE-2008-1803


Description: 
 ===========================================================  Ubuntu Security Notice USN-646-1         September 18, 2008 rdesktop vulnerabilities CVE-2008-1801, CVE-2008-1802, CVE-2008-1803 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   rdesktop                        1.4.1-1.1ubuntu0.6.06.1  Ubuntu 7.04:   rdesktop                        1.5.0-1ubuntu1.1  Ubuntu 7.10:   rdesktop                        1.5.0-2ubuntu0.1  Ubuntu 8.04 LTS:   rdesktop                        1.5.0-3+cvs20071006ubuntu0.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that rdesktop did not properly validate the length of packet headers when processing RDP requests. If a user were tricked into connecting to a malicious server, an attacker could cause a denial of service or possible execute arbitrary code with the privileges of the user. (CVE-2008-1801)  Multiple buffer overflows were discovered in rdesktop when processing RDP redirect requests. If a user were tricked into connecting to a malicious server, an attacker could cause a denial of service or possible execute arbitrary code with the privileges of the user. (CVE-2008-1802)  It was discovered that rdesktop performed a signed integer comparison when reallocating dynamic buffers which could result in a heap-based overflow. If a user were tricked into connecting to a malicious server, an attacker could cause a denial of service or possible execute arbitrary code with the privileges of the user. (CVE-2008-1802) 





[More...](http://www.ubuntu.com/usn/usn-646-1)

---

