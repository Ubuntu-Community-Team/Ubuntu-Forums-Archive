---
title: "USN-821-1: Firefox and Xulrunner vulnerabilities"
date: 2009-09-10
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-09-10
Referenced CVEs: 
                                       CVE-2009-3070, CVE-2009-3071, CVE-2009-3072, CVE-2009-3074, CVE-2009-3075, CVE-2009-3076, CVE-2009-3077, CVE-2009-3078, CVE-2009-3079        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-821-1         September 10, 2009 firefox-3.0, xulrunner-1.9 vulnerabilities CVE-2009-3070, CVE-2009-3071, CVE-2009-3072, CVE-2009-3074, CVE-2009-3075, CVE-2009-3076, CVE-2009-3077, CVE-2009-3078, CVE-2009-3079 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   firefox-3.0                     3.0.14+build2+nobinonly-0ubuntu0.8.04.1   xulrunner-1.9                   1.9.0.14+build2+nobinonly-0ubuntu0.8.04.1  Ubuntu 8.10:   abrowser                        3.0.14+build2+nobinonly-0ubuntu0.8.10.1   firefox-3.0                     3.0.14+build2+nobinonly-0ubuntu0.8.10.1   xulrunner-1.9                   1.9.0.14+build2+nobinonly-0ubuntu0.8.10.1  Ubuntu 9.04:   abrowser                        3.0.14+build2+nobinonly-0ubuntu0.9.04.1   firefox-3.0                     3.0.14+build2+nobinonly-0ubuntu0.9.04.1   xulrunner-1.9                   1.9.0.14+build2+nobinonly-0ubuntu0.9.04.1  After a standard system upgrade you need to restart Firefox and any applications that use xulrunner, such as Epiphany, to effect the necessary changes.  Details follow:  Several flaws were discovered in the Firefox browser and JavaScript engines. If a user were tricked into viewing a malicious website, a remote attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-3070, CVE-2009-3071, CVE-2009-3072, CVE-2009-3074, CVE-2009-3075)  Jesse Ruderman and Dan Kaminsky discovered that Firefox did not adequately inform users when security modules were added or removed via PKCS11. If a user visited a malicious website, an attacker could exploit this to trick the user into installing a malicious PKCS11 module. (CVE-2009-3076)  It was discovered that Firefox did not properly manage memory when using XUL tree elements. If a user were tricked into viewing a malicious website, a remote attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-3077)  Juan Pablo Lopez Yacubian discovered that Firefox did properly display certain Unicode characters in the location bar and other text fields when using a certain non-Ubuntu font. If a user configured Firefox to use this font, an attacker could exploit this to spoof the location bar, such as in a phishing attack. (CVE-2009-3078)  It was discovered that the BrowserFeedWriter in Firefox could be subverted to run JavaScript code from web content with elevated chrome privileges. If a user were tricked into viewing a malicious website, an attacker could exploit this to execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-3079) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-821-1)

---

