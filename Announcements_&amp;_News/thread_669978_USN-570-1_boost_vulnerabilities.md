---
title: "USN-570-1: boost vulnerabilities"
date: 2008-01-16
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-01-16
Referenced CVEs:
CVE-2008-0171, CVE-2008-0172


Description:
 ===========================================================  Ubuntu Security Notice USN-570-1           January 16, 2008 boost vulnerabilities CVE-2008-0171, CVE-2008-0172 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libboost-regex1.33.1            1.33.1-2ubuntu0.1  Ubuntu 6.10:   libboost-regex1.33.1            1.33.1-7ubuntu1.1  Ubuntu 7.04:   libboost-regex1.33.1            1.33.1-9ubuntu3.1  Ubuntu 7.10:   libboost-regex1.34.1            1.34.1-2ubuntu1.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Will Drewry and Tavis Ormandy discovered that the boost library  did not properly perform input validation on regular expressions. An attacker could send a specially crafted regular expression to an application linked against boost and cause a denial of service via application crash. 





[More...](http://www.ubuntu.com/usn/usn-570-1)

---

