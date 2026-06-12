---
title: "USN-728-3: Firefox vulnerabilities"
date: 2009-03-06
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-03-06
Referenced CVEs: 
CVE-2009-0772, CVE-2009-0774, CVE-2009-0776


Description: 
 =========================================================== Ubuntu Security Notice USN-728-3             March 06, 2009 firefox vulnerabilities CVE-2009-0772, CVE-2009-0774, CVE-2009-0776 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   firefox                         1.5.dfsg+1.5.0.15~prepatch080614k-0ubuntu1  After a standard system upgrade you need to restart Firefox to effect the necessary changes.  Details follow:  Jesse Ruderman and Gary Kwong discovered flaws in the browser engine. If a user were tricked into viewing a malicious website, a remote attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-0772, CVE-2009-0774)  Georgi Guninski discovered a flaw when Firefox performed a cross-domain redirect. An attacker could bypass the same-origin policy in Firefox by utilizing nsIRDFService and steal private data from users authenticated to the redirected website. (CVE-2009-0776) 





[More...](http://www.ubuntu.com/usn/usn-728-3)

---

