---
title: "USN-775-2: Quagga regression"
date: 2009-06-09
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-06-09
Description: 
                                        =========================================================== Ubuntu Security Notice USN-775-2              June 09, 2009 quagga regression [https://launchpad.net/bugs/384193](https://launchpad.net/bugs/384193) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   quagga                          0.99.2-1ubuntu3.6  Ubuntu 8.04 LTS:   quagga                          0.99.9-2ubuntu1.3  Ubuntu 8.10:   quagga                          0.99.9-6ubuntu0.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  USN-775-1 fixed vulnerabilities in Quagga.  The preventative fixes introduced in Quagga prior to Ubuntu 9.04 could result in BGP service failures.  This update fixes the problem.  We apologize for the inconvenience.  Original advisory details:   It was discovered that the BGP service in Quagga did not correctly  handle certain AS paths containing 4-byte ASNs.  An authenticated remote  attacker could exploit this flaw to cause bgpd to abort, leading to a  denial of service. 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-775-2)

---

