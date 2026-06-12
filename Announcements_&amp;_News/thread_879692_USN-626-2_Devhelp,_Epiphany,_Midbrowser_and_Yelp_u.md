---
title: "USN-626-2: Devhelp, Epiphany, Midbrowser and Yelp update"
date: 2008-08-04
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-08-04
Description: 
 ===========================================================  Ubuntu Security Notice USN-626-2            August 04, 2008 devhelp, epiphany-browser, midbrowser, yelp update [https://launchpad.net/bugs/253462](https://launchpad.net/bugs/253462) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   devhelp                         0.19-1ubuntu1.8.04.3   epiphany-gecko                  2.22.2-0ubuntu0.8.04.5   midbrowser                      0.3.0rc1a-1~8.04.2   yelp                            2.22.1-0ubuntu2.8.04.2  After a standard system upgrade you need to restart Devhelp, Epiphany, Midbrowser and Yelp to effect the necessary changes.  Details follow:  USN-626-1 fixed vulnerabilities in xulrunner-1.9. The changes required that Devhelp, Epiphany, Midbrowser and Yelp also be updated to use the new xulrunner-1.9.  Original advisory details:   A flaw was discovered in the browser engine. A variable could be made to  overflow causing the browser to crash. If a user were tricked into opening  a malicious web page, an attacker could cause a denial of service or  possibly execute arbitrary code with the privileges of the user invoking  the program. (CVE-2008-2785)    Billy Rios discovered that Firefox and xulrunner, as used by browsers  such as Epiphany, did not properly perform URI splitting with pipe  symbols when passed a command-line URI. If Firefox or xulrunner were  passed a malicious URL, an attacker may be able to execute local  content with chrome privileges. (CVE-2008-2933) 





[More...](http://www.ubuntu.com/usn/usn-626-2)

---

