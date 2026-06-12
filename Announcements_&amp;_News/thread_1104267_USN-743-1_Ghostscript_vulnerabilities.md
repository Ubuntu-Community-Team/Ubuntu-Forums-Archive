---
title: "USN-743-1: Ghostscript vulnerabilities"
date: 2009-03-23
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-03-23
Referenced CVEs: 
CVE-2009-0583, CVE-2009-0584


Description: 
=========================================================== Ubuntu Security Notice USN-743-1             March 23, 2009 ghostscript, gs-gpl vulnerabilities CVE-2009-0583, CVE-2009-0584 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   gs-gpl                          8.15-4ubuntu3.2  Ubuntu 7.10:   libgs8                          8.61.dfsg.1~svn8187-0ubuntu3.5  Ubuntu 8.04 LTS:   libgs8                          8.61.dfsg.1-1ubuntu3.1  Ubuntu 8.10:   libgs8                          8.63.dfsg.1-0ubuntu6.3  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that Ghostscript contained multiple integer overflows in its ICC color management library. If a user or automated system were tricked into opening a crafted Postscript file, an attacker could cause a denial of service or execute arbitrary code with privileges of the user invoking the program. (CVE-2009-0583)  It was discovered that Ghostscript did not properly perform bounds checking in its ICC color management library. If a user or automated system were tricked into opening a crafted Postscript file, an attacker could cause a denial of service or execute arbitrary code with privileges of the user invoking the program. (CVE-2009-0584)





[More...](http://www.ubuntu.com/usn/USN-743-1)

---

