---
title: "USN-493-1: Firefox vulnerabilities"
date: 2007-07-31
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-07-31
Referenced CVEs:
CVE-2007-3844, CVE-2007-3845


Description:
 ===========================================================  Ubuntu Security Notice USN-493-1              July 31, 2007 firefox vulnerabilities CVE-2007-3844, CVE-2007-3845 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   firefox                        1.5.dfsg+1.5.0.13~prepatch070731-0ubuntu1  Ubuntu 6.10:   firefox                        2.0.0.6+0dfsg-0ubuntu0.6.10  Ubuntu 7.04:   firefox                        2.0.0.6+1-0ubuntu1  After a standard system upgrade you need to restart Firefox to effect the necessary changes.  Details follow:  A flaw was discovered in handling of "about:blank" windows used by addons.  A malicious web site could exploit this to modify the contents, or steal confidential data (such as passwords), of other web pages. (CVE-2007-3844)  Jesper Johansson discovered that spaces and double-quotes were not correctly handled when launching external programs.  In rare configurations, after tricking a user into opening a malicious web page, an attacker could execute helpers with arbitrary arguments with the user's privileges.  (CVE-2007-3845) 





[More...](http://www.ubuntu.com/usn/usn-493-1)

---

