---
title: "USN-623-1: Firefox vulnerabilities"
date: 2008-07-17
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-07-17
Referenced CVEs: 
CVE-2008-2785, CVE-2008-2933


Description: 
=========================================================== Ubuntu Security Notice USN-623-1              July 17, 2008firefox vulnerabilitiesCVE-2008-2785, CVE-2008-2933===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSUbuntu 7.04Ubuntu 7.10This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  firefox                         1.5.dfsg+1.5.0.15~prepatch080614d-0ubuntu1Ubuntu 7.04:  firefox                         2.0.0.16+0nobinonly-0ubuntu0.7.4Ubuntu 7.10:  firefox                         2.0.0.16+1nobinonly-0ubuntu0.7.10After a standard system upgrade you need to restart Firefox to effect thenecessary changes.Details follow:A flaw was discovered in the browser engine. A variable could be made tooverflow causing the browser to crash. If a user were tricked into openinga malicious web page, an attacker could cause a denial of service orpossibly execute arbitrary code with the privileges of the user invokingthe program. (CVE-2008-2785)Billy Rios discovered that Firefox did not properly perform URI splittingwith pipe symbols when passed a command-line URI. If Firefox were passeda malicious URL, an attacker may be able to execute local content withchrome privileges. (CVE-2008-2933)





[More...](http://www.ubuntu.com/usn/usn-623-1)

---

