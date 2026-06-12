---
title: "USN-802-2: Apache regression"
date: 2009-08-19
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-08-19
Referenced CVEs: 
                                       [https://launchpad.net/bugs/409987](https://launchpad.net/bugs/409987)        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-802-2            August 19, 2009 apache2 regression [https://launchpad.net/bugs/409987](https://launchpad.net/bugs/409987) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   apache2-common                  2.0.55-4ubuntu2.8   apache2-mpm-perchild            2.0.55-4ubuntu2.8   apache2-mpm-prefork             2.0.55-4ubuntu2.8   apache2-mpm-worker              2.0.55-4ubuntu2.8   libapr0                         2.0.55-4ubuntu2.8  Ubuntu 8.04 LTS:   apache2-mpm-event               2.2.8-1ubuntu0.11   apache2-mpm-perchild            2.2.8-1ubuntu0.11   apache2-mpm-prefork             2.2.8-1ubuntu0.11   apache2-mpm-worker              2.2.8-1ubuntu0.11   apache2.2-common                2.2.8-1ubuntu0.11  Ubuntu 8.10:   apache2-mpm-event               2.2.9-7ubuntu3.3   apache2-mpm-prefork             2.2.9-7ubuntu3.3   apache2-mpm-worker              2.2.9-7ubuntu3.3   apache2.2-common                2.2.9-7ubuntu3.3  Ubuntu 9.04:   apache2-mpm-event               2.2.11-2ubuntu2.3   apache2-mpm-prefork             2.2.11-2ubuntu2.3   apache2-mpm-worker              2.2.11-2ubuntu2.3   apache2.2-common                2.2.11-2ubuntu2.3  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  USN-802-1 fixed vulnerabilities in Apache. The upstream fix for CVE-2009-1891 introduced a regression that would cause Apache children to occasionally segfault when mod_deflate is used. This update fixes the problem.  We apologize for the inconvenience.  Original advisory details:   It was discovered that mod_proxy_http did not properly handle a large  amount of streamed data when used as a reverse proxy. A remote attacker  could exploit this and cause a denial of service via memory resource  consumption. This issue affected Ubuntu 8.04 LTS, 8.10 and 9.04.  (CVE-2009-1890)    It was discovered that mod_deflate did not abort compressing large files  when the connection was closed. A remote attacker could exploit this and  cause a denial of service via CPU resource consumption. (CVE-2009-1891)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-802-2)

---

