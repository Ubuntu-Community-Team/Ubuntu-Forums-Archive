---
title: "USN-745-1: Firefox and Xulrunner vulnerabilities"
date: 2009-03-28
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-03-28
Referenced CVEs: 
                                       CVE-2009-1044, CVE-2009-1169        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-745-1             March 28, 2009 firefox, firefox-3.0, xulrunner-1.9 vulnerabilities CVE-2009-1044, CVE-2009-1169 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   firefox                         1.5.dfsg+1.5.0.15~prepatch080614l-0ubuntu1  Ubuntu 7.10:   firefox                         2.0.0.21~tb.21.308+nobinonly-0ubuntu0.7.10.1  Ubuntu 8.04 LTS:   firefox-3.0                     3.0.8+nobinonly-0ubuntu0.8.04.2   xulrunner-1.9                   1.9.0.8+nobinonly-0ubuntu0.8.04.1  Ubuntu 8.10:   abrowser                        3.0.8+nobinonly-0ubuntu0.8.10.2   firefox-3.0                     3.0.8+nobinonly-0ubuntu0.8.10.2   xulrunner-1.9                   1.9.0.8+nobinonly-0ubuntu0.8.10.1  After a standard system upgrade you need to restart Firefox and any applications that use xulrunner, such as Epiphany, to effect the necessary changes.  Details follow:  It was discovered that Firefox did not properly perform XUL garbage collection. If a user were tricked into viewing a malicious website, a remote attacker could cause a denial of service or execute arbitrary code with the privileges of the user invoking the program. This issue only affected Ubuntu 8.04 LTS and 8.10. (CVE-2009-1044)  A flaw was discovered in the way Firefox performed XSLT transformations. If a user were tricked into opening a crafted XSL stylesheet, an attacker could cause a denial of service or execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-1169) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-745-1)

---

