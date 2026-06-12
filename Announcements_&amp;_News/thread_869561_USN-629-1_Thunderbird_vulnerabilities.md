---
title: "USN-629-1: Thunderbird vulnerabilities"
date: 2008-07-24
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-07-24
Referenced CVEs: 
CVE-2008-2785, CVE-2008-2798, CVE-2008-2799, CVE-2008-2802, CVE-2008-2803, CVE-2008-2807, CVE-2008-2809, CVE-2008-2811


Description: 
 ===========================================================  Ubuntu Security Notice USN-629-1              July 25, 2008 mozilla-thunderbird, thunderbird vulnerabilities CVE-2008-2785, CVE-2008-2798, CVE-2008-2799, CVE-2008-2802, CVE-2008-2803, CVE-2008-2807, CVE-2008-2809, CVE-2008-2811 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   mozilla-thunderbird             1.5.0.13+1.5.0.15~prepatch080614d-0ubuntu0.6.06.1  Ubuntu 7.04:   mozilla-thunderbird             1.5.0.13+1.5.0.15~prepatch080614d-0ubuntu0.7.04.1  Ubuntu 7.10:   thunderbird                     2.0.0.16+nobinonly-0ubuntu0.7.10.1  Ubuntu 8.04 LTS:   thunderbird                     2.0.0.16+nobinonly-0ubuntu0.8.04.1  After a standard system upgrade you need to restart Thunderbird to effect the necessary changes.  Details follow:  Various flaws were discovered in the browser engine. If a user had Javascript enabled and were tricked into opening a malicious web page, an attacker could cause a denial of service via application crash, or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-2798, CVE-2008-2799)  It was discovered that Thunderbird would allow non-privileged XUL documents to load chrome scripts from the fastload file if Javascript was enabled. This could allow an attacker to execute arbitrary Javascript code with chrome privileges. (CVE-2008-2802)  A flaw was discovered in Thunderbird that allowed overwriting trusted objects via mozIJSSubScriptLoader.loadSubScript(). If a user had Javascript enabled and was tricked into opening a malicious web page, an attacker could execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-2803)  Daniel Glazman found that an improperly encoded .properties file in an add-on can result in uninitialized memory being used. If a user were tricked into installing a malicious add-on, Thunderbird may be able to see data from other programs. (CVE-2008-2807)  John G. Myers discovered a weakness in the trust model used by Thunderbird regarding alternate names on self-signed certificates. If a user were tricked into accepting a certificate containing alternate name entries, an attacker could impersonate another server. (CVE-2008-2809)  A vulnerability was discovered in the block reflow code of Thunderbird. If a user enabled Javascript, this vulnerability could be used by an attacker to cause a denial of service via application crash, or execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-2811)  A flaw was discovered in the browser engine. A variable could be made to overflow causing Thunderbird to crash. If a user enable Javascript and was tricked into opening a malicious web page, an attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-2785)  Mozilla developers audited the MIME handling code looking for similar vulnerabilities to the previously fixed CVE-2008-0304, and changed several function calls to use safer versions of string routines. 





[More...](http://www.ubuntu.com/usn/usn-629-1)

---

