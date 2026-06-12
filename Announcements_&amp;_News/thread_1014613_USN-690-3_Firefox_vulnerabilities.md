---
title: "USN-690-3: Firefox vulnerabilities"
date: 2008-12-18
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-12-18
Referenced CVEs: 
CVE-2008-5500, CVE-2008-5503, CVE-2008-5506, CVE-2008-5507, CVE-2008-5511, CVE-2008-5512


Description: 
 =========================================================== Ubuntu Security Notice USN-690-3          December 18, 2008 firefox vulnerabilities CVE-2008-5500, CVE-2008-5503, CVE-2008-5506, CVE-2008-5507, CVE-2008-5511, CVE-2008-5512 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   firefox                         1.5.dfsg+1.5.0.15~prepatch080614i-0ubuntu1  After a standard system upgrade you need to restart Firefox to effect the necessary changes.  Details follow:  Several flaws were discovered in the browser engine. These problems could allow an attacker to crash the browser and possibly execute arbitrary code with user privileges. (CVE-2008-5500)  Boris Zbarsky discovered that the same-origin check in Firefox could be bypassed by utilizing XBL-bindings. An attacker could exploit this to read data from other domains. (CVE-2008-5503)  Marius Schilder discovered that Firefox did not properly handle redirects to an outside domain when an XMLHttpRequest was made to a same-origin resource. It's possible that sensitive information could be revealed in the XMLHttpRequest response. (CVE-2008-5506)  Chris Evans discovered that Firefox did not properly protect a user's data when accessing a same-domain Javascript URL that is redirected to an unparsable Javascript off-site resource. If a user were tricked into opening a malicious website, an attacker may be able to steal a limited amount of private data. (CVE-2008-5507)  Several flaws were discovered in the Javascript engine. If a user were tricked into opening a malicious website, an attacker could exploit this to execute arbitrary Javascript code within the context of another website or with chrome privileges. (CVE-2008-5511, CVE-2008-5512) 





[More...](http://www.ubuntu.com/usn/usn-690-3)

---

