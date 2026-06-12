---
title: "USN-755-1: Kerberos vulnerabilities"
date: 2009-04-08
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-04-08
Referenced CVEs: 
                                       CVE-2009-0844, CVE-2009-0845, CVE-2009-0846, CVE-2009-0847        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-755-1             April 07, 2009 krb5 vulnerabilities CVE-2009-0844, CVE-2009-0845, CVE-2009-0846, CVE-2009-0847 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libkadm55                       1.4.3-5ubuntu0.8   libkrb53                        1.4.3-5ubuntu0.8  Ubuntu 7.10:   libkadm55                       1.6.dfsg.1-7ubuntu0.2   libkrb53                        1.6.dfsg.1-7ubuntu0.2  Ubuntu 8.04 LTS:   libkadm55                       1.6.dfsg.3~beta1-2ubuntu1.1   libkrb53                        1.6.dfsg.3~beta1-2ubuntu1.1  Ubuntu 8.10:   libkadm55                       1.6.dfsg.4~beta1-3ubuntu0.1   libkrb53                        1.6.dfsg.4~beta1-3ubuntu0.1  After a standard system upgrade you need to restart any services using the Kerberos libraries to effect the necessary changes.  Details follow:  Multiple flaws were discovered in the Kerberos GSS-API and ASN.1 routines that did not correctly handle certain requests. An unauthenticated remote attacker could send specially crafted traffic to crash services using the Kerberos library, leading to a denial of service. 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-755-1)

---

