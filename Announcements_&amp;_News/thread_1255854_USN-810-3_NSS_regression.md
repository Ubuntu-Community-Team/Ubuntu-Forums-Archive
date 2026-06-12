---
title: "USN-810-3: NSS regression"
date: 2009-09-02
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-09-02
Description: 
                                        =========================================================== Ubuntu Security Notice USN-810-3         September 02, 2009 nss regression [https://launchpad.net/bugs/409864](https://launchpad.net/bugs/409864) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   libnss3-1d                      3.12.3.1-0ubuntu0.8.04.2  Ubuntu 8.10:   libnss3-1d                      3.12.3.1-0ubuntu0.8.10.2  Ubuntu 9.04:   libnss3-1d                      3.12.3.1-0ubuntu0.9.04.2  After a standard system upgrade you need to restart any applications that use NSS, such as Firefox, to effect the necessary changes.  Details follow:  USN-810-1 fixed vulnerabilities in NSS.  Jozsef Kadlecsik noticed that the new libraries on amd64 did not correctly set stack memory flags, and caused applications using NSS (e.g. Firefox) to have an executable stack. This reduced the effectiveness of some defensive security protections.  This update fixes the problem.  We apologize for the inconvenience.  Original advisory details:   Moxie Marlinspike discovered that NSS did not properly handle regular  expressions in certificate names. A remote attacker could create a  specially crafted certificate to cause a denial of service (via application  crash) or execute arbitrary code as the user invoking the program.  (CVE-2009-2404)   Moxie Marlinspike and Dan Kaminsky independently discovered that NSS did  not properly handle certificates with NULL characters in the certificate  name. An attacker could exploit this to perform a man in the middle attack  to view sensitive information or alter encrypted communications.  (CVE-2009-2408)   Dan Kaminsky discovered NSS would still accept certificates with MD2 hash  signatures. As a result, an attacker could potentially create a malicious  trusted certificate to impersonate another site. (CVE-2009-2409) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-810-3)

---

