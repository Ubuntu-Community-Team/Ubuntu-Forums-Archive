---
title: "USN-742-1: JasPer vulnerabilities"
date: 2009-03-19
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-03-19
Referenced CVEs: 
CVE-2008-3520, CVE-2008-3521, CVE-2008-3522


Description: 
=========================================================== Ubuntu Security Notice USN-742-1             March 19, 2009 jasper vulnerabilities CVE-2008-3520, CVE-2008-3521, CVE-2008-3522 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libjasper-1.701-1               1.701.0-2ubuntu0.6.06.1  Ubuntu 7.10:   libjasper1                      1.900.1-3ubuntu0.7.10.1  Ubuntu 8.04 LTS:   libjasper1                      1.900.1-3ubuntu0.8.04.1  Ubuntu 8.10:   libjasper1                      1.900.1-5ubuntu0.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that JasPer did not correctly handle memory allocation when parsing certain malformed JPEG2000 images. If a user were tricked into opening a specially crafted image with an application that uses libjasper, an attacker could cause a denial of service and possibly execute arbitrary code with the user's privileges. (CVE-2008-3520)  It was discovered that JasPer created temporary files in an insecure way. Local users could exploit a race condition and cause a denial of service in libjasper applications. (CVE-2008-3521)  It was discovered that JasPer did not correctly handle certain formatting operations. If a user were tricked into opening a specially crafted image with an application that uses libjasper, an attacker could cause a denial of service and possibly execute arbitrary code with the user's privileges. (CVE-2008-3522)





[More...](http://www.ubuntu.com/usn/USN-742-1)

---

