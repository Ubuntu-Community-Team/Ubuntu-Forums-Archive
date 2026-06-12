---
title: "USN-827-1: Dnsmasq vulnerabilities"
date: 2009-09-01
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-09-01
Referenced CVEs: 
                                       CVE-2009-2957, CVE-2009-2958        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-827-1         September 01, 2009 dnsmasq vulnerabilities CVE-2009-2957, CVE-2009-2958 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   dnsmasq-base                    2.41-2ubuntu2.2  Ubuntu 8.10:   dnsmasq-base                    2.45-1ubuntu1.1  Ubuntu 9.04:   dnsmasq-base                    2.47-3ubuntu0.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  IvAin Arce, Pablo HernAin Jorge, Alejandro Pablo Rodriguez, MartA*n Coco, Alberto SoliAto Testa and Pablo Annetta discovered that Dnsmasq did not properly validate its input when processing TFTP requests for files with long names. A remote attacker could cause a denial of service or execute arbitrary code with user privileges. Dnsmasq runs as the 'dnsmasq' user by default on Ubuntu. (CVE-2009-2957)  Steve Grubb discovered that Dnsmasq could be made to dereference a NULL pointer when processing certain TFTP requests. A remote attacker could cause a denial of service by sending a crafted TFTP request. (CVE-2009-2958) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-827-1)

---

