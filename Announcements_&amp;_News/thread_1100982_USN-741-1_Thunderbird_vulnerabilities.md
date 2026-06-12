---
title: "USN-741-1: Thunderbird vulnerabilities"
date: 2009-03-19
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-03-19
Referenced CVEs: 
CVE-2009-0352, CVE-2009-0772, CVE-2009-0774, CVE-2009-0776


Description: 
===========================================================Ubuntu Security Notice USN-741-1             March 19, 2009mozilla-thunderbird, thunderbird vulnerabilitiesCVE-2009-0352, CVE-2009-0772, CVE-2009-0774, CVE-2009-0776===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSUbuntu 7.10Ubuntu 8.04 LTSUbuntu 8.10This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  mozilla-thunderbird             1.5.0.13+1.5.0.15~prepatch080614k-0ubuntu0.6.06.1Ubuntu 7.10:  thunderbird                     2.0.0.21+nobinonly-0ubuntu0.7.10.1Ubuntu 8.04 LTS:  thunderbird                     2.0.0.21+nobinonly-0ubuntu0.8.04.1Ubuntu 8.10:  thunderbird                     2.0.0.21+nobinonly-0ubuntu0.8.10.1After a standard system upgrade you need to restart Thunderbird to effectthe necessary changes.Details follow:Several flaws were discovered in the browser engine. If Javascript wereenabled, an attacker could exploit these flaws to crash Thunderbird andpossibly execute arbitrary code with user privileges. (CVE-2009-0352)Jesse Ruderman and Gary Kwong discovered flaws in the browser engine. If auser had Javascript enabled, these problems could allow a remote attacker tocause a denial of service or possibly execute arbitrary code with theprivileges of the user invoking the program. (CVE-2009-0772, CVE-2009-0774)Georgi Guninski discovered a flaw when Thunderbird performed a cross-domainredirect. If a user had Javascript enabled, an attacker could bypass thesame-origin policy in Thunderbird by utilizing nsIRDFService and stealprivate data from users authenticated to the redirected website.(CVE-2009-0776)





[More...](http://www.ubuntu.com/usn/usn-741-1)

---

