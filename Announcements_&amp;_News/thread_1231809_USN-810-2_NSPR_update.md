---
title: "USN-810-2: NSPR update"
date: 2009-08-04
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-08-04
Description: 
                                        =========================================================== Ubuntu Security Notice USN-810-2            August 04, 2009 nspr update [https://launchpad.net/bugs/387745](https://launchpad.net/bugs/387745) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   libnspr4-0d                     4.7.5-0ubuntu0.8.04.1  Ubuntu 8.10:   libnspr4-0d                     4.7.5-0ubuntu0.8.10.1  Ubuntu 9.04:   libnspr4-0d                     4.7.5-0ubuntu0.9.04.1  After a standard system upgrade you need to restart any applications that use NSPR, such as Firefox, to effect the necessary changes.  Details follow:  USN-810-1 fixed vulnerabilities in NSS. This update provides the NSPR needed to use the new NSS.  Original advisory details:   Moxie Marlinspike discovered that NSS did not properly handle regular  expressions in certificate names. A remote attacker could create a  specially crafted certificate to cause a denial of service (via application  crash) or execute arbitrary code as the user invoking the program.  (CVE-2009-2404)    Moxie Marlinspike and Dan Kaminsky independently discovered that NSS did  not properly handle certificates with NULL characters in the certificate  name. An attacker could exploit this to perform a man in the middle attack  to view sensitive information or alter encrypted communications.  (CVE-2009-2408)    Dan Kaminsky discovered NSS would still accept certificates with MD2 hash  signatures. As a result, an attacker could potentially create a malicious  trusted certificate to impersonate another site. (CVE-2009-2409) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-810-2)

---

