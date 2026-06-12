---
title: "USN-690-1: Firefox and xulrunner vulnerabilities"
date: 2008-12-17
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-12-17
Referenced CVEs: 
CVE-2008-5500, CVE-2008-5501, CVE-2008-5502, CVE-2008-5505, CVE-2008-5506, CVE-2008-5507, CVE-2008-5508, CVE-2008-5510, CVE-2008-5511, CVE-2008-5512, CVE-2008-5513


Description: 
 =========================================================== Ubuntu Security Notice USN-690-1          December 17, 2008 firefox-3.0, xulrunner-1.9 vulnerabilities CVE-2008-5500, CVE-2008-5501, CVE-2008-5502, CVE-2008-5505, CVE-2008-5506, CVE-2008-5507, CVE-2008-5508, CVE-2008-5510, CVE-2008-5511, CVE-2008-5512, CVE-2008-5513 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   firefox-3.0                     3.0.5+nobinonly-0ubuntu0.8.04.1   xulrunner-1.9                   1.9.0.5+nobinonly-0ubuntu0.8.04.1  Ubuntu 8.10:   abrowser                        3.0.5+nobinonly-0ubuntu0.8.10.1   firefox-3.0                     3.0.5+nobinonly-0ubuntu0.8.10.1   xulrunner-1.9                   1.9.0.5+nobinonly-0ubuntu0.8.10.1  After a standard system upgrade you need to restart Firefox and any applications that use xulrunner, such as Epiphany, to effect the necessary changes.  Details follow:  Several flaws were discovered in the browser engine. These problems could allow an attacker to crash the browser and possibly execute arbitrary code with user privileges. (CVE-2008-5500, CVE-2008-5501, CVE-2008-5502)  It was discovered that Firefox did not properly handle persistent cookie data. If a user were tricked into opening a malicious website, an attacker could write persistent data in the user's browser and track the user across browsing sessions. (CVE-2008-5505)  Marius Schilder discovered that Firefox did not properly handle redirects to an outside domain when an XMLHttpRequest was made to a same-origin resource. It's possible that sensitive information could be revealed in the XMLHttpRequest response. (CVE-2008-5506)  Chris Evans discovered that Firefox did not properly protect a user's data when accessing a same-domain Javascript URL that is redirected to an unparsable Javascript off-site resource. If a user were tricked into opening a malicious website, an attacker may be able to steal a limited amount of private data. (CVE-2008-5507)  Chip Salzenberg, Justin Schuh, Tom Cross, and Peter William discovered Firefox did not properly parse URLs when processing certain control characters. (CVE-2008-5508)  Kojima Hajime discovered that Firefox did not properly handle an escaped null character. An attacker may be able to exploit this flaw to bypass script sanitization. (CVE-2008-5510)  Several flaws were discovered in the Javascript engine. If a user were tricked into opening a malicious website, an attacker could exploit this to execute arbitrary Javascript code within the context of another website or with chrome privileges. (CVE-2008-5511, CVE-2008-5512)  Flaws were discovered in the session-restore feature of Firefox. If a user were tricked into opening a malicious website, an attacker could exploit this to perform cross-site scripting attacks or execute arbitrary Javascript code with chrome privileges. (CVE-2008-5513) 





[More...](http://www.ubuntu.com/usn/usn-690-1)

---

