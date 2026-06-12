---
title: "USN-546-1: Firefox vulnerabilities"
date: 2007-11-27
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-11-27
Referenced CVEs:
CVE-2007-5947, CVE-2007-5959, CVE-2007-5960


Description:
 ===========================================================  Ubuntu Security Notice USN-546-1          November 26, 2007 firefox vulnerabilities CVE-2007-5947, CVE-2007-5959, CVE-2007-5960 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   firefox                         1.5.dfsg+1.5.0.14~prepatch071125a-0ubuntu1  Ubuntu 6.10:   firefox                         2.0.0.10+0nobinonly-0ubuntu0.6.10  Ubuntu 7.04:   firefox                         2.0.0.10+1nobinonly-0ubuntu1  Ubuntu 7.10:   firefox                         2.0.0.10+2nobinonly-0ubuntu1.7.10.1  After a standard system upgrade you need to restart Firefox to effect the necessary changes.  Details follow:  It was discovered that Firefox incorrectly associated redirected sites as the origin of "jar:" contents. A malicious web site could exploit this to modify or steal confidential data (such as passwords) from other web sites. (CVE-2007-5947)  Various flaws were discovered in the layout and JavaScript engines. By tricking a user into opening a malicious web page, an attacker could execute arbitrary code with the user's privileges. (CVE-2007-5959)  Gregory Fleischer discovered that it was possible to use JavaScript to manipulate Firefox's Referer header.  A malicious web site could exploit this to conduct cross-site request forgeries against sites that relied only on Referer headers for protection from such attacks. (CVE-2007-5960) 





[More...](http://www.ubuntu.com/usn/usn-546-1)

---

