---
title: "USN-779-1: Firefox and Xulrunner vulnerabilities"
date: 2009-06-12
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-06-12
Referenced CVEs: 
                                       CVE-2009-1832, CVE-2009-1833, CVE-2009-1834, CVE-2009-1835, CVE-2009-1836, CVE-2009-1837, CVE-2009-1838, CVE-2009-1839, CVE-2009-1840, CVE-2009-1841        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-779-1              June 12, 2009 firefox-3.0, xulrunner-1.9 vulnerabilities CVE-2009-1832, CVE-2009-1833, CVE-2009-1834, CVE-2009-1835, CVE-2009-1836, CVE-2009-1837, CVE-2009-1838, CVE-2009-1839, CVE-2009-1840, CVE-2009-1841 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   firefox-3.0                     3.0.11+build2+nobinonly-0ubuntu0.8.04.1   xulrunner-1.9                   1.9.0.11+build2+nobinonly-0ubuntu0.8.04.1  Ubuntu 8.10:   abrowser                        3.0.11+build2+nobinonly-0ubuntu0.8.10.1   firefox-3.0                     3.0.11+build2+nobinonly-0ubuntu0.8.10.1   xulrunner-1.9                   1.9.0.11+build2+nobinonly-0ubuntu0.8.10.2  Ubuntu 9.04:   abrowser                        3.0.11+build2+nobinonly-0ubuntu0.9.04.1   firefox-3.0                     3.0.11+build2+nobinonly-0ubuntu0.9.04.1   xulrunner-1.9                   1.9.0.11+build2+nobinonly-0ubuntu0.9.04.1  After a standard system upgrade you need to restart Firefox and any applications that use xulrunner, such as Epiphany, to effect the necessary changes.  Details follow:  Several flaws were discovered in the browser and JavaScript engines of Firefox. If a user were tricked into viewing a malicious website, a remote attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-1392, CVE-2009-1832, CVE-2009-1833, CVE-2009-1837, CVE-2009-1838)  Pavel Cvrcek discovered that Firefox would sometimes display certain invalid Unicode characters as whitespace. An attacker could exploit this to spoof the location bar, such as in a phishing attack. (CVE-2009-1834)  Gregory Fleischer, Adam Barth and Collin Jackson discovered that Firefox would allow access to local files from resources loaded via the file: protocol. If a user were tricked into downloading then opening a malicious file, an attacker could steal potentially sensitive information. (CVE-2009-1835, CVE-2009-1839)  Shuo Chen, Ziqing Mao, Yi-Min Wang, and Ming Zhang discovered that Firefox did not properly handle error responses when connecting to a proxy server. If a remote attacker were able to perform a man-in-the-middle attack, this flaw could be exploited to view sensitive information. (CVE-2009-1836)  Wladimir Palant discovered Firefox did not check content-loading policies when loading external script files into XUL documents. As a result, Firefox might load malicious content under certain circumstances. (CVE-2009-1840)  It was discovered that Firefox could be made to run scripts with elevated privileges. If a user were tricked into viewing a malicious website, an attacker could cause a chrome privileged object, such as the browser sidebar, to run arbitrary code via interactions with the attacker controlled website. (CVE-2009-1841) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-779-1)

---

