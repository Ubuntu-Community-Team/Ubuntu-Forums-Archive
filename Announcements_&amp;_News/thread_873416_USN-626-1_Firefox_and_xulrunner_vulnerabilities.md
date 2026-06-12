---
title: "USN-626-1: Firefox and xulrunner vulnerabilities"
date: 2008-07-29
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-07-29
Referenced CVEs: 
CVE-2008-2785, CVE-2008-2933, CVE-2008-2934


Description: 
=========================================================== Ubuntu Security Notice USN-626-1              July 29, 2008firefox-3.0, xulrunner-1.9 vulnerabilitiesCVE-2008-2785, CVE-2008-2933, CVE-2008-2934===========================================================A security issue affects the following Ubuntu releases:Ubuntu 8.04 LTSThis advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 8.04 LTS:  firefox-3.0                     3.0.1+build1+nobinonly-0ubuntu0.8.04.3  xulrunner-1.9                   1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3After a standard system upgrade you need to restart Firefox and anyapplications that use xulrunner, such as Epiphany, to effect thenecessary changes.Details follow:A flaw was discovered in the browser engine. A variable could be made tooverflow causing the browser to crash. If a user were tricked into openinga malicious web page, an attacker could cause a denial of service orpossibly execute arbitrary code with the privileges of the user invokingthe program. (CVE-2008-2785)Billy Rios discovered that Firefox and xulrunner, as used by browserssuch as Epiphany, did not properly perform URI splitting with pipesymbols when passed a command-line URI. If Firefox or xulrunner werepassed a malicious URL, an attacker may be able to execute localcontent with chrome privileges. (CVE-2008-2933)





[More...](http://www.ubuntu.com/usn/usn-626-1)

---

