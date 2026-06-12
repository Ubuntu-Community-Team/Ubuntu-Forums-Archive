---
title: "USN-777-1: Ntp vulnerabilities"
date: 2009-05-19
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-05-19
Referenced CVEs: 
                                       CVE-2009-0159, CVE-2009-1252        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-777-1               May 19, 2009 ntp vulnerabilities CVE-2009-0159, CVE-2009-1252 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   ntp                             1:4.2.0a+stable-8.1ubuntu6.2   ntp-server                      1:4.2.0a+stable-8.1ubuntu6.2  Ubuntu 8.04 LTS:   ntp                             1:4.2.4p4+dfsg-3ubuntu2.2  Ubuntu 8.10:   ntp                             1:4.2.4p4+dfsg-6ubuntu2.3  Ubuntu 9.04:   ntp                             1:4.2.4p4+dfsg-7ubuntu5.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  A stack-based buffer overflow was discovered in ntpq. If a user were tricked into connecting to a malicious ntp server, a remote attacker could cause a denial of service in ntpq, or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-0159)  Chris Ries discovered a stack-based overflow in ntp. If ntp was configured to use autokey, a remote attacker could send a crafted packet to cause a denial of service, or possibly execute arbitrary code. (CVE-2009-1252) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-777-1)

---

