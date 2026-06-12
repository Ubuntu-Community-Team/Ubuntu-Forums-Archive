---
title: "USN-701-1: Thunderbird vulnerabilities"
date: 2009-01-06
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-01-06
Referenced CVEs: 
CVE-2008-5500, CVE-2008-5503, CVE-2008-5506, CVE-2008-5507, CVE-2008-5508, CVE-2008-5510, CVE-2008-5511, CVE-2008-5512


Description: 
 =========================================================== Ubuntu Security Notice USN-701-1           January 06, 2009 thunderbird vulnerabilities CVE-2008-5500, CVE-2008-5503, CVE-2008-5506, CVE-2008-5507, CVE-2008-5508, CVE-2008-5510, CVE-2008-5511, CVE-2008-5512 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 7.10:   thunderbird                     2.0.0.19+nobinonly-0ubuntu0.7.10.1  Ubuntu 8.04 LTS:   thunderbird                     2.0.0.19+nobinonly-0ubuntu0.8.04.1  Ubuntu 8.10:   thunderbird                     2.0.0.19+nobinonly-0ubuntu0.8.10.1  After a standard system upgrade you need to restart Thunderbird to effect the necessary changes.  Details follow:  Several flaws were discovered in the browser engine. If a user had Javascript enabled, these problems could allow an attacker to crash Thunderbird and possibly execute arbitrary code with user privileges. (CVE-2008-5500)  Boris Zbarsky discovered that the same-origin check in Thunderbird could be bypassed by utilizing XBL-bindings. If a user had Javascript enabled, an attacker could exploit this to read data from other domains. (CVE-2008-5503)  Marius Schilder discovered that Thunderbird did not properly handle redirects to an outside domain when an XMLHttpRequest was made to a same-origin resource. When Javascript is enabled, it's possible that sensitive information could be revealed in the XMLHttpRequest response. (CVE-2008-5506)  Chris Evans discovered that Thunderbird did not properly protect a user's data when accessing a same-domain Javascript URL that is redirected to an unparsable Javascript off-site resource. If a user were tricked into opening a malicious website and had Javascript enabled, an attacker may be able to steal a limited amount of private data. (CVE-2008-5507)  Chip Salzenberg, Justin Schuh, Tom Cross, and Peter William discovered Thunderbird did not properly parse URLs when processing certain control characters. (CVE-2008-5508)  Kojima Hajime discovered that Thunderbird did not properly handle an escaped null character. An attacker may be able to exploit this flaw to bypass script sanitization. (CVE-2008-5510)  Several flaws were discovered in the Javascript engine. If a user were tricked into opening a malicious website and had Javascript enabled, an attacker could exploit this to execute arbitrary Javascript code within the context of another website or with chrome privileges. (CVE-2008-5511, CVE-2008-5512) 





[More...](http://www.ubuntu.com/usn/usn-701-1)

---

