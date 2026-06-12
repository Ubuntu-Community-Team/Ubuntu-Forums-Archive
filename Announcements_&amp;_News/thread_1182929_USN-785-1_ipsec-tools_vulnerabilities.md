---
title: "USN-785-1: ipsec-tools vulnerabilities"
date: 2009-06-09
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-06-09
Referenced CVEs: 
                                       CVE-2009-1574, CVE-2009-1632        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-785-1              June 09, 2009 ipsec-tools vulnerabilities CVE-2009-1574, CVE-2009-1632 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   racoon                          1:0.6.5-4ubuntu1.3  Ubuntu 8.04 LTS:   racoon                          1:0.6.7-1.1ubuntu1.2  Ubuntu 8.10:   racoon                          1:0.7-2.1ubuntu1.8.10.1  Ubuntu 9.04:   racoon                          1:0.7-2.1ubuntu1.9.04.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that ipsec-tools did not properly handle certain fragmented packets. A remote attacker could send specially crafted packets to the server and cause a denial of service. (CVE-2009-1574)  It was discovered that ipsec-tools did not properly handle memory usage when verifying certificate signatures or processing nat-traversal keep-alive messages. A remote attacker could send specially crafted packets to the server and exhaust available memory, leading to a denial of service. (CVE-2009-1632)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-785-1)

---

