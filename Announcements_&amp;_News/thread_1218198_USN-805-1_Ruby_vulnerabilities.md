---
title: "USN-805-1: Ruby vulnerabilities"
date: 2009-07-20
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-07-20
Referenced CVEs: 
                                       CVE-2009-0642, CVE-2009-1904        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-805-1              July 20, 2009 ruby1.8, ruby1.9 vulnerabilities CVE-2009-0642, CVE-2009-1904 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libruby1.8                      1.8.4-1ubuntu1.7   ruby1.8                         1.8.4-1ubuntu1.7  Ubuntu 8.04 LTS:   libruby1.8                      1.8.6.111-2ubuntu1.3   ruby1.8                         1.8.6.111-2ubuntu1.3  Ubuntu 8.10:   libruby1.8                      1.8.7.72-1ubuntu0.2   libruby1.9                      1.9.0.2-7ubuntu1.2   ruby1.8                         1.8.7.72-1ubuntu0.2   ruby1.9                         1.9.0.2-7ubuntu1.2  Ubuntu 9.04:   libruby1.8                      1.8.7.72-3ubuntu0.1   libruby1.9                      1.9.0.2-9ubuntu1.1   ruby1.8                         1.8.7.72-3ubuntu0.1   ruby1.9                         1.9.0.2-9ubuntu1.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that Ruby did not properly validate certificates. An attacker could exploit this and present invalid or revoked X.509 certificates. (CVE-2009-0642)  It was discovered that Ruby did not properly handle string arguments that represent large numbers. An attacker could exploit this and cause a denial of service. (CVE-2009-1904)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-805-1)

---

