---
title: "USN-717-1: Firefox and Xulrunner vulnerabilities"
date: 2009-02-10
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-02-10
Referenced CVEs: 
CVE-2009-0352, CVE-2009-0353, CVE-2009-0354, CVE-2009-0355, CVE-2009-0357, CVE-2009-0358


Description: 
 =========================================================== Ubuntu Security Notice USN-717-1          February 10, 2009 firefox-3.0, xulrunner-1.9 vulnerabilities CVE-2009-0352, CVE-2009-0353, CVE-2009-0354, CVE-2009-0355, CVE-2009-0357, CVE-2009-0358 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   firefox-3.0                     3.0.6+nobinonly-0ubuntu0.8.04.1   xulrunner-1.9                   1.9.0.6+nobinonly-0ubuntu0.8.04.1  Ubuntu 8.10:   abrowser                        3.0.6+nobinonly-0ubuntu0.8.10.1   firefox-3.0                     3.0.6+nobinonly-0ubuntu0.8.10.1   xulrunner-1.9                   1.9.0.6+nobinonly-0ubuntu0.8.10.1  After a standard system upgrade you need to restart Firefox and any applications that use xulrunner, such as Epiphany, to effect the necessary changes.  Details follow:  Several flaws were discovered in the browser engine. These problems could allow an attacker to crash the browser and possibly execute arbitrary code with user privileges. (CVE-2009-0352, CVE-2009-0353)  A flaw was discovered in the JavaScript engine. An attacker could bypass the same-origin policy in Firefox by utilizing a chrome XBL method and execute arbitrary JavaScript within the context of another website. (CVE-2009-0354)  A flaw was discovered in the browser engine when restoring closed tabs. If a user were tricked into restoring a tab to a malicious website with form input controls, an attacker could steal local files on the user's system. (CVE-2009-0355)  Wladimir Palant discovered that Firefox did not restrict access to cookies in HTTP response headers. If a user were tricked into opening a malicious web page, a remote attacker could view sensitive information. (CVE-2009-0357)  Paul Nel discovered that Firefox did not honor certain Cache-Control HTTP directives. A local attacker could exploit this to view private data in improperly cached pages of another user. (CVE-2009-0358) 





[More...](http://www.ubuntu.com/usn/usn-717-1)

---

