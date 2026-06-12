---
title: "USN-647-1: Thunderbird vulnerabilities"
date: 2008-09-26
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-09-26
Referenced CVEs: 
CVE-2008-3835, CVE-2008-4058, CVE-2008-4059, CVE-2008-4060, CVE-2008-4061, CVE-2008-4062, CVE-2008-4063, CVE-2008-4064, CVE-2008-4065, CVE-2008-4066, CVE-2008-4067, CVE-2008-4068, CVE-2008-4070


Description: 
 ===========================================================  Ubuntu Security Notice USN-647-1         September 26, 2008 mozilla-thunderbird, thunderbird vulnerabilities CVE-2008-3835, CVE-2008-4058, CVE-2008-4059, CVE-2008-4060, CVE-2008-4061, CVE-2008-4062, CVE-2008-4063, CVE-2008-4064, CVE-2008-4065, CVE-2008-4066, CVE-2008-4067, CVE-2008-4068, CVE-2008-4070 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   mozilla-thunderbird             1.5.0.13+1.5.0.15~prepatch080614g-0ubuntu0.6.06.1  Ubuntu 7.04:   mozilla-thunderbird             1.5.0.13+1.5.0.15~prepatch080614g-0ubuntu0.7.04.1  Ubuntu 7.10:   thunderbird                     2.0.0.17+nobinonly-0ubuntu0.7.10.1  Ubuntu 8.04 LTS:   thunderbird                     2.0.0.17+nobinonly-0ubuntu0.8.04.1  After a standard system upgrade you need to restart Thunderbird to effect the necessary changes.  Details follow:  It was discovered that the same-origin check in Thunderbird could be bypassed. If a user had JavaScript enabled and were tricked into opening a malicious website, an attacker may be able to execute JavaScript in the context of a different website. (CVE-2008-3835)  Several problems were discovered in the browser engine of Thunderbird. If a user had JavaScript enabled, this could allow an attacker to execute code with chrome privileges. (CVE-2008-4058, CVE-2008-4059, CVE-2008-4060)  Drew Yao, David Maciejak and other Mozilla developers found several problems in the browser engine of Thunderbird. If a user had JavaScript enabled and were tricked into opening a malicious web page, an attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-4061, CVE-2008-4062, CVE-2008-4063, CVE-2008-4064)  Dave Reed discovered a flaw in the JavaScript parsing code when processing certain BOM characters. An attacker could exploit this to bypass script filters and perform cross-site scripting attacks if a user had JavaScript enabled. (CVE-2008-4065)  Gareth Heyes discovered a flaw in the HTML parser of Thunderbird. If a user had JavaScript enabled and were tricked into opening a malicious web page, an attacker could bypass script filtering and perform cross-site scripting attacks. (CVE-2008-4066)  Boris Zbarsky and Georgi Guninski independently discovered flaws in the resource: protocol. An attacker could exploit this to perform directory traversal, read information about the system, and prompt the user to save information in a file. (CVE-2008-4067, CVE-2008-4068)  Georgi Guninski discovered that Thunderbird improperly handled cancelled newsgroup messages. If a user opened a crafted newsgroup message, an attacker could cause a buffer overrun and potentially execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-4070) 





[More...](http://www.ubuntu.com/usn/usn-647-1)

---

