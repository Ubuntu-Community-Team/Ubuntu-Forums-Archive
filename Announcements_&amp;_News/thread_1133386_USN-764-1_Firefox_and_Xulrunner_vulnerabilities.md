---
title: "USN-764-1: Firefox and Xulrunner vulnerabilities"
date: 2009-04-22
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-04-22
Referenced CVEs: 
                                       CVE-2009-0652, CVE-2009-1302, CVE-2009-1303, CVE-2009-1304, CVE-2009-1305, CVE-2009-1306, CVE-2009-1307, CVE-2009-1308, CVE-2009-1309, CVE-2009-1310, CVE-2009-1311, CVE-2009-1312        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-764-1             April 23, 2009 firefox-3.0, xulrunner-1.9 vulnerabilities CVE-2009-0652, CVE-2009-1302, CVE-2009-1303, CVE-2009-1304, CVE-2009-1305, CVE-2009-1306, CVE-2009-1307, CVE-2009-1308, CVE-2009-1309, CVE-2009-1310, CVE-2009-1311, CVE-2009-1312 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   firefox-3.0                     3.0.9+nobinonly-0ubuntu0.8.04.1   xulrunner-1.9                   1.9.0.9+nobinonly-0ubuntu0.8.04.1  Ubuntu 8.10:   abrowser                        3.0.9+nobinonly-0ubuntu0.8.10.1   firefox-3.0                     3.0.9+nobinonly-0ubuntu0.8.10.1   xulrunner-1.9                   1.9.0.9+nobinonly-0ubuntu0.8.10.1  Ubuntu 9.04:   abrowser                        3.0.9+nobinonly-0ubuntu0.9.04.1   firefox-3.0                     3.0.9+nobinonly-0ubuntu0.9.04.1   xulrunner-1.9                   1.9.0.9+nobinonly-0ubuntu0.9.04.1  After a standard system upgrade you need to restart Firefox and any applications that use xulrunner, such as Epiphany, to effect the necessary changes.  Details follow:  Several flaws were discovered in the browser engine. If a user were tricked into viewing a malicious website, a remote attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-1302, CVE-2009-1303, CVE-2009-1304, CVE-2009-1305)  It was discovered that Firefox displayed certain Unicode characters which could be visually confused with punctuation in valid web addresses in the location bar. An attacker could exploit this to spoof the location bar, such as in a phishing attack. (CVE-2009-0652)  Several flaws were discovered in the way Firefox processed malformed URI schemes. If a user were tricked into viewing a malicious website, a remote attacker could execute arbitrary JavaScript or steal private data. (CVE-2009-1306, CVE-2009-1307, CVE-2009-1309, CVE-2009-1310, CVE-2009-1312)  Cefn Hoile discovered Firefox did not adequately protect against embedded third-party stylesheets. An attacker could exploit this to perform script injection attacks using XBL bindings. (CVE-2009-1308)  Paolo Amadini discovered that Firefox would submit POST data when reloading an inner frame of a web page. If a user were tricked into viewing a malicious website, a remote attacker could steal private data. (CVE-2009-1311) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-764-1)

---

