---
title: "USN-787-1: Apache vulnerabilities"
date: 2009-06-11
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-06-11
Referenced CVEs: 
                                       CVE-2009-0023, CVE-2009-1191, CVE-2009-1195, CVE-2009-1955, CVE-2009-1956        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-787-1              June 12, 2009 apache2 vulnerabilities CVE-2009-0023, CVE-2009-1191, CVE-2009-1195, CVE-2009-1955, CVE-2009-1956 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   apache2-common                  2.0.55-4ubuntu2.5   apache2-mpm-perchild            2.0.55-4ubuntu2.5   apache2-mpm-prefork             2.0.55-4ubuntu2.5   apache2-mpm-worker              2.0.55-4ubuntu2.5   libapr0                         2.0.55-4ubuntu2.5  Ubuntu 8.04 LTS:   apache2-mpm-event               2.2.8-1ubuntu0.8   apache2-mpm-perchild            2.2.8-1ubuntu0.8   apache2-mpm-prefork             2.2.8-1ubuntu0.8   apache2-mpm-worker              2.2.8-1ubuntu0.8   apache2.2-common                2.2.8-1ubuntu0.8  Ubuntu 8.10:   apache2-mpm-event               2.2.9-7ubuntu3.1   apache2-mpm-prefork             2.2.9-7ubuntu3.1   apache2-mpm-worker              2.2.9-7ubuntu3.1   apache2.2-common                2.2.9-7ubuntu3.1  Ubuntu 9.04:   apache2-mpm-event               2.2.11-2ubuntu2.1   apache2-mpm-prefork             2.2.11-2ubuntu2.1   apache2-mpm-worker              2.2.11-2ubuntu2.1   apache2.2-common                2.2.11-2ubuntu2.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Matthew Palmer discovered an underflow flaw in apr-util as included in Apache. An attacker could cause a denial of service via application crash in Apache using a crafted SVNMasterURI directive, .htaccess file, or when using mod_apreq2. This issue only affected Ubuntu 6.06 LTS. (CVE-2009-0023)  Sander de Boer discovered that mod_proxy_ajp would reuse connections when a client closed a connection without sending a request body. A remote attacker could exploit this to obtain sensitive response data. This issue only affected Ubuntu 9.04. (CVE-2009-1191)  Jonathan Peatfield discovered that Apache did not process Includes options correctly. With certain configurations of Options and AllowOverride, a local attacker could use an .htaccess file to override intended restrictions and execute arbitrary code via a Server-Side-Include file. This issue affected Ubuntu 8.04 LTS, 8.10 and 9.04. (CVE-2009-1195)  It was discovered that the XML parser did not properly handle entity expansion. A remote attacker could cause a denial of service via memory resource consumption by sending a crafted request to an Apache server configured to use mod_dav or mod_dav_svn. This issue only affected Ubuntu 6.06 LTS. (CVE-2009-1955)  C. Michael Pilato discovered an off-by-one buffer overflow in apr-util when formatting certain strings. For big-endian machines (powerpc, hppa and sparc in Ubuntu), a remote attacker could cause a denial of service or information disclosure leak. All other architectures for Ubuntu are not considered to be at risk. This issue only affected Ubuntu 6.06 LTS. (CVE-2009-1956) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-787-1)

---

