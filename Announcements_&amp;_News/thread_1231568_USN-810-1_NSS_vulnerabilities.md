---
title: "USN-810-1: NSS vulnerabilities"
date: 2009-08-04
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-08-04
Referenced CVEs: 
                                       CVE-2009-2404, CVE-2009-2408, CVE-2009-2409        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-810-1            August 04, 2009 nss vulnerabilities CVE-2009-2404, CVE-2009-2408, CVE-2009-2409 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   libnss3-1d                      3.12.3.1-0ubuntu0.8.04.1  Ubuntu 8.10:   libnss3-1d                      3.12.3.1-0ubuntu0.8.10.1  Ubuntu 9.04:   libnss3-1d                      3.12.3.1-0ubuntu0.9.04.1  After a standard system upgrade you need to restart an applications that use NSS, such as Firefox, to effect the necessary changes.  Details follow:  Moxie Marlinspike discovered that NSS did not properly handle regular expressions in certificate names. A remote attacker could create a specially crafted certificate to cause a denial of service (via application crash) or execute arbitrary code as the user invoking the program. (CVE-2009-2404)  Moxie Marlinspike and Dan Kaminsky independently discovered that NSS did not properly handle certificates with NULL characters in the certificate name. An attacker could exploit this to perform a man in the middle attack to view sensitive information or alter encrypted communications. (CVE-2009-2408)  Dan Kaminsky discovered NSS would still accept certificates with MD2 hash signatures. As a result, an attacker could potentially create a malicious trusted certificate to impersonate another site. (CVE-2009-2409) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-810-1)

---

