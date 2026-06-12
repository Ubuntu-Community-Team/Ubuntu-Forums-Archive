---
title: "USN-642-1: Postfix vulnerabilities"
date: 2008-09-10
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-09-10
Referenced CVEs: 
CVE-2008-3889


Description: 
 ===========================================================  Ubuntu Security Notice USN-642-1         September 10, 2008 postfix vulnerabilities CVE-2008-3889 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 7.10:   postfix                         2.4.5-3ubuntu1.3  Ubuntu 8.04 LTS:   postfix                         2.5.1-2ubuntu1.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Wietse Venema discovered that Postfix leaked internal file descriptors when executing non-Postfix commands.  A local attacker could exploit this to cause Postfix to run out of descriptors, leading to a denial of service. 





[More...](http://www.ubuntu.com/usn/usn-642-1)

---

