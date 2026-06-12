---
title: "USN-673-1: libxml2 vulnerabilities"
date: 2008-11-18
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-11-18
Referenced CVEs: 
CVE-2008-4225, CVE-2008-4226


Description: 
 =========================================================== Ubuntu Security Notice USN-673-1          November 19, 2008 libxml2 vulnerabilities CVE-2008-4225, CVE-2008-4226 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libxml2                         2.6.24.dfsg-1ubuntu1.4  Ubuntu 7.10:   libxml2                         2.6.30.dfsg-2ubuntu1.4  Ubuntu 8.04 LTS:   libxml2                         2.6.31.dfsg-2ubuntu1.3  Ubuntu 8.10:   libxml2                         2.6.32.dfsg-4ubuntu1.1  After a standard system upgrade you need to restart your sessions to effect the necessary changes.  Details follow:  Drew Yao discovered that libxml2 did not correctly handle certain corrupt XML documents.  If a user or automated system were tricked into processing a malicious XML document, a remote attacker could cause applications linked against libxml2 to enter an infinite loop, leading to a denial of service. (CVE-2008-4225)  Drew Yao discovered that libxml2 did not correctly handle large memory allocations.  If a user or automated system were tricked into processing a very large XML document, a remote attacker could cause applications linked against libxml2 to crash, leading to a denial of service. (CVE-2008-4226) 





[More...](http://www.ubuntu.com/usn/usn-673-1)

---

