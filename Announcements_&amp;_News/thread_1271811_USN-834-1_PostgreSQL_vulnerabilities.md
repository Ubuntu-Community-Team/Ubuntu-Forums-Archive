---
title: "USN-834-1: PostgreSQL vulnerabilities"
date: 2009-09-21
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-09-21
Referenced CVEs: 
                                       CVE-2009-3229, CVE-2009-3230, CVE-2009-3231        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-834-1         September 21, 2009 postgresql-8.1, postgresql-8.3 vulnerabilities CVE-2009-3229, CVE-2009-3230, CVE-2009-3231 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   postgresql-8.1                  8.1.18-0ubuntu0.6.06  Ubuntu 8.04 LTS:   postgresql-8.3                  8.3.8-0ubuntu8.04  Ubuntu 8.10:   postgresql-8.3                  8.3.8-0ubuntu8.10  Ubuntu 9.04:   postgresql-8.3                  8.3.8-0ubuntu9.04  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that PostgreSQL could be made to unload and reload an already loaded module by using the LOAD command. A remote authenticated attacker could exploit this to cause a denial of service. This issue did not affect Ubuntu 6.06 LTS. (CVE-2009-3229)  Due to an incomplete fix for CVE-2007-6600, RESET ROLE and RESET SESSION AUTHORIZATION operations were allowed inside security-definer functions. A remote authenticated attacker could exploit this to escalate privileges within PostgreSQL. (CVE-2009-3230)  It was discovered that PostgreSQL did not properly perform LDAP authentication under certain circumstances. When configured to use LDAP with anonymous binds, a remote attacker could bypass authentication by supplying an empty password. This issue did not affect Ubuntu 6.06 LTS. (CVE-2009-3231) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-834-1)

---

