---
title: "USN-546-2: Firefox regression"
date: 2007-12-04
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-12-04
Description:
 ===========================================================  Ubuntu Security Notice USN-546-2          December 04, 2007 firefox regression [https://bugzilla.mozilla.org/show_bug.cgi?id=405584](https://bugzilla.mozilla.org/show_bug.cgi?id=405584) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.10 Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.10:   firefox                         2.0.0.11+0nobinonly-0ubuntu0.6.10  Ubuntu 7.04:   firefox                         2.0.0.11+1nobinonly-0ubuntu0.7.4  Ubuntu 7.10:   firefox                         2.0.0.11+2nobinonly-0ubuntu0.7.10  After a standard system upgrade you need to restart Firefox to effect the necessary changes.  Details follow:  USN-546-1 fixed vulnerabilities in Firefox. The upstream update included a faulty patch which caused the drawImage method of the canvas element to fail.  This update fixes the problem.  We apologize for the inconvenience.  Original advisory details:   It was discovered that Firefox incorrectly associated redirected sites  as the origin of "jar:" contents. A malicious web site could exploit this  to modify or steal confidential data (such as passwords) from other web  sites. (CVE-2007-5947)    Various flaws were discovered in the layout and JavaScript engines. By  tricking a user into opening a malicious web page, an attacker could  execute arbitrary code with the user's privileges. (CVE-2007-5959)    Gregory Fleischer discovered that it was possible to use JavaScript to  manipulate Firefox's Referer header.  A malicious web site could exploit  this to conduct cross-site request forgeries against sites that relied  only on Referer headers for protection from such attacks. (CVE-2007-5960) 





[More...](http://www.ubuntu.com/usn/usn-546-2)

---

