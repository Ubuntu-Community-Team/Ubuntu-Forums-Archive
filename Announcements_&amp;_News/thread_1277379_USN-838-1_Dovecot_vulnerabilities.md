---
title: "USN-838-1: Dovecot vulnerabilities"
date: 2009-09-28
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-09-28
Referenced CVEs: 
                                       CVE-2008-4577, CVE-2008-5301, CVE-2009-2632, CVE-2009-3235        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-838-1         September 28, 2009 dovecot vulnerabilities CVE-2008-4577, CVE-2008-5301, CVE-2009-2632, CVE-2009-3235 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   dovecot-common                  1:1.0.10-1ubuntu5.2  Ubuntu 8.10:   dovecot-common                  1:1.1.4-0ubuntu1.3  Ubuntu 9.04:   dovecot-common                  1:1.1.11-0ubuntu4.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that the ACL plugin in Dovecot would incorrectly handle negative access rights. An attacker could exploit this flaw to access the Dovecot server, bypassing the indended access restrictions. This only affected Ubuntu 8.04 LTS. (CVE-2008-4577)  It was discovered that the ManageSieve service in Dovecot incorrectly handled ".." in script names. A remote attacker could exploit this to read and modify arbitrary sieve files on the server. This only affected Ubuntu 8.10. (CVE-2008-5301)  It was discovered that the Sieve plugin in Dovecot incorrectly handled certain sieve scripts. An authenticated user could exploit this with a crafted sieve script to cause a denial of service or possibly execute arbitrary code. (CVE-2009-2632, CVE-2009-3235)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-838-1)

---

