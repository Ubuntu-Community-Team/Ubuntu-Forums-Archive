---
title: "USN-621-1: Ruby vulnerabilities"
date: 2008-06-26
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-06-26
Referenced CVEs: 
CVE-2008-2662, CVE-2008-2663, CVE-2008-2664, CVE-2008-2725, CVE-2008-2726


Description: 
 ===========================================================  Ubuntu Security Notice USN-621-1              June 26, 2008 ruby1.8 vulnerabilities CVE-2008-2662, CVE-2008-2663, CVE-2008-2664, CVE-2008-2725, CVE-2008-2726 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libruby1.8                      1.8.4-1ubuntu1.5   ruby1.8                         1.8.4-1ubuntu1.5  Ubuntu 7.04:   libruby1.8                      1.8.5-4ubuntu2.2   ruby1.8                         1.8.5-4ubuntu2.2  Ubuntu 7.10:   libruby1.8                      1.8.6.36-1ubuntu3.2   ruby1.8                         1.8.6.36-1ubuntu3.2  Ubuntu 8.04 LTS:   libruby1.8                      1.8.6.111-2ubuntu1.1   ruby1.8                         1.8.6.111-2ubuntu1.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Drew Yao discovered several vulnerabilities in Ruby which lead to integer overflows. If a user or automated system were tricked into running a malicious script, an attacker could cause a denial of service or execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-2662, CVE-2008-2663, CVE-2008-2725, CVE-2008-2726)  Drew Yao discovered that Ruby did not sanitize its input when using ALLOCA. If a user or automated system were tricked into running a malicious script, an attacker could cause a denial of service via memory corruption. (CVE-2008-2664) 





[More...](http://www.ubuntu.com/usn/usn-621-1)

---

