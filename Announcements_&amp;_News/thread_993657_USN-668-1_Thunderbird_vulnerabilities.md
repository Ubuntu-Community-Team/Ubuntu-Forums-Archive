---
title: "USN-668-1: Thunderbird vulnerabilities"
date: 2008-11-26
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-11-26
Referenced CVEs: 
CVE-2008-5012 CVE-2008-5014 CVE-2008-5016 CVE-2008-5017 CVE-2008-5018 CVE-2008-5021 CVE-2008-5022 CVE-2008-5024


Description: 
=========================================================== Ubuntu Security Notice USN-668-1          November 26, 2008 mozilla-thunderbird, thunderbird vulnerabilities CVE-2008-5012, CVE-2008-5014, CVE-2008-5016, CVE-2008-5017, CVE-2008-5018, CVE-2008-5021, CVE-2008-5022, CVE-2008-5024 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   mozilla-thunderbird             1.5.0.13+1.5.0.15~prepatch080614h-0ubuntu0.6.06.1  Ubuntu 7.10:   thunderbird                     2.0.0.18+nobinonly-0ubuntu0.7.10.1  Ubuntu 8.04 LTS:   thunderbird                     2.0.0.18+nobinonly-0ubuntu0.8.04.1  Ubuntu 8.10:   thunderbird                     2.0.0.18+nobinonly-0ubuntu0.8.10.1  After a standard system upgrade you need to restart Thunderbird to effect the necessary changes.  Georgi Guninski, Michal Zalewsk and Chris Evans discovered that the same-origin check in Thunderbird could be bypassed. If a user were tricked into opening a malicious website, an attacker could obtain private information from data stored in the images, or discover information about software on the user's computer. (CVE-2008-5012)  Jesse Ruderman discovered that Thunderbird did not properly guard locks on non-native objects. If a user had JavaScript enabled and were tricked into opening malicious web content, an attacker could cause a browser crash and possibly execute arbitrary code with user privileges. (CVE-2008-5014)  Several problems were discovered in the browser, layout and JavaScript engines. If a user had JavaScript enabled, these problems could allow an attacker to crash Thunderbird and possibly execute arbitrary code with user privileges. (CVE-2008-5016, CVE-2008-5017, CVE-2008-5018)  A flaw was discovered in Thunderbird's DOM constructing code. If a user were tricked into opening a malicious website while having JavaScript enabled, an attacker could cause the browser to crash and potentially execute arbitrary code with user privileges. (CVE-2008-5021)  It was discovered that the same-origin check in Thunderbird could be bypassed. If a user had JavaScript enabled and were tricked into opening malicious web content, an attacker could execute JavaScript in the context of a different website. (CVE-2008-5022)  Chris Evans discovered that Thunderbird did not properly parse E4X documents, leading to quote characters in the namespace not being properly escaped. (CVE-2008-5024)  Boris Zbarsky discovered that Thunderbird did not properly process comments in forwarded in-line messages. If a user had JavaScript enabled and opened a malicious email, an attacker may be able to obtain information about the recipient. 





[More...](http://www.ubuntu.com/usn/usn-668-1)

---

