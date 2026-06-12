---
title: "USN-701-2: Thunderbird vulnerabilities"
date: 2009-01-07
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-01-07
Referenced CVEs: 
CVE-2008-5500, CVE-2008-5503, CVE-2008-5506, CVE-2008-5507, CVE-2008-5508, CVE-2008-5511, CVE-2008-5512


Description: 
===========================================================Ubuntu Security Notice USN-701-2           January 06, 2009mozilla-thunderbird vulnerabilitiesCVE-2008-5500, CVE-2008-5503, CVE-2008-5506, CVE-2008-5507,CVE-2008-5508, CVE-2008-5511, CVE-2008-5512===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSThis advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  mozilla-thunderbird             1.5.0.13+1.5.0.15~prepatch080614i-0ubuntu0.6.06.1After a standard system upgrade you need to restart Thunderbird to effectthe necessary changes.Details follow:Several flaws were discovered in the browser engine. If a user had Javascriptenabled, these problems could allow an attacker to crash Thunderbird andpossibly execute arbitrary code with user privileges. (CVE-2008-5500)Boris Zbarsky discovered that the same-origin check in Thunderbird could bebypassed by utilizing XBL-bindings. If a user had Javascript enabled, anattacker could exploit this to read data from other domains. (CVE-2008-5503)Marius Schilder discovered that Thunderbird did not properly handle redirectsto an outside domain when an XMLHttpRequest was made to a same-origin resource.When Javascript is enabled, it's possible that sensitive information could berevealed in the XMLHttpRequest response. (CVE-2008-5506)Chris Evans discovered that Thunderbird did not properly protect a user's datawhen accessing a same-domain Javascript URL that is redirected to an unparsableJavascript off-site resource. If a user were tricked into opening a maliciouswebsite and had Javascript enabled, an attacker may be able to steal a limitedamount of private data. (CVE-2008-5507)Chip Salzenberg, Justin Schuh, Tom Cross, and Peter William discoveredThunderbird did not properly parse URLs when processing certain controlcharacters. (CVE-2008-5508)Several flaws were discovered in the Javascript engine. If a user were trickedinto opening a malicious website and had Javascript enabled, an attacker couldexploit this to execute arbitrary Javascript code within the context of anotherwebsite or with chrome privileges. (CVE-2008-5511, CVE-2008-5512)





[More...](http://www.ubuntu.com/usn/usn-701-2)

---

