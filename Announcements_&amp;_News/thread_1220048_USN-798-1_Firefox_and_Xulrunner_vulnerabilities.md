---
title: "USN-798-1: Firefox and Xulrunner vulnerabilities"
date: 2009-07-22
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-07-22
Referenced CVEs: 
                                       CVE-2009-2462, CVE-2009-2463, CVE-2009-2464, CVE-2009-2465, CVE-2009-2466, CVE-2009-2467, CVE-2009-2469, CVE-2009-2472        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-798-1              July 22, 2009 firefox-3.0, xulrunner-1.9 vulnerabilities CVE-2009-2462, CVE-2009-2463, CVE-2009-2464, CVE-2009-2465, CVE-2009-2466, CVE-2009-2467, CVE-2009-2469, CVE-2009-2472 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   firefox-3.0                     3.0.12+build1+nobinonly-0ubuntu0.8.04.1   xulrunner-1.9                   1.9.0.12+build1+nobinonly-0ubuntu0.8.04.1  Ubuntu 8.10:   abrowser                        3.0.12+build1+nobinonly-0ubuntu0.8.10.1   firefox-3.0                     3.0.12+build1+nobinonly-0ubuntu0.8.10.1   xulrunner-1.9                   1.9.0.12+build1+nobinonly-0ubuntu0.8.10.2  Ubuntu 9.04:   abrowser                        3.0.12+build1+nobinonly-0ubuntu0.9.04.1   firefox-3.0                     3.0.12+build1+nobinonly-0ubuntu0.9.04.1   xulrunner-1.9                   1.9.0.12+build1+nobinonly-0ubuntu0.9.04.1  After a standard system upgrade you need to restart Firefox and any applications that use xulrunner, such as Epiphany, to effect the necessary changes.  Details follow:  Several flaws were discovered in the Firefox browser and JavaScript engines. If a user were tricked into viewing a malicious website, a remote attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-2462, CVE-2009-2463, CVE-2009-2464, CVE-2009-2465, CVE-2009-2466, CVE-2009-2469)  Attila Suszter discovered a flaw in the way Firefox processed Flash content. If a user were tricked into viewing and navigating within a specially crafted Flash object, a remote attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-2467)  It was discovered that Firefox did not properly handle some SVG content. An attacker could exploit this to cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-2469)  A flaw was discovered in the JavaScript engine. If a user were tricked into viewing a malicious website, an attacker could exploit this perform cross-site scripting attacks. (CVE-2009-2472) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-798-1)

---

