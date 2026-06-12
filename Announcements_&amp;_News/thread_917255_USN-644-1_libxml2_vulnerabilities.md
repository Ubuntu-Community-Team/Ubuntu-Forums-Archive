---
title: "USN-644-1: libxml2 vulnerabilities"
date: 2008-09-11
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-09-11
Referenced CVEs: 
CVE-2008-3281, CVE-2008-3529


Description: 
 ===========================================================  Ubuntu Security Notice USN-644-1         September 11, 2008 libxml2 vulnerabilities CVE-2008-3281, CVE-2008-3529 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libxml2                         2.6.24.dfsg-1ubuntu1.3  Ubuntu 7.04:   libxml2                         2.6.27.dfsg-1ubuntu3.3  Ubuntu 7.10:   libxml2                         2.6.30.dfsg-2ubuntu1.3  Ubuntu 8.04 LTS:   libxml2                         2.6.31.dfsg-2ubuntu1.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that libxml2 did not correctly handle long entity names. If a user were tricked into processing a specially crafted XML document, a remote attacker could execute arbitrary code with user privileges or cause the application linked against libxml2 to crash, leading to a denial of service. (CVE-2008-3529)  USN-640-1 fixed vulnerabilities in libxml2.  When processing extremely large XML documents with valid entities, it was possible to incorrectly trigger the newly added vulnerability protections.  This update fixes the problem.  (CVE-2008-3281) 





[More...](http://www.ubuntu.com/usn/usn-644-1)

---

