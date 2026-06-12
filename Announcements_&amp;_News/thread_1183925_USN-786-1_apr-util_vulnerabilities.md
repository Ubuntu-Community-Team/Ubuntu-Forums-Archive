---
title: "USN-786-1: apr-util vulnerabilities"
date: 2009-06-10
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-06-10
Referenced CVEs: 
                                       CVE-2009-0023, CVE-2009-1955, CVE-2009-1956        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-786-1              June 10, 2009 apr-util vulnerabilities CVE-2009-0023, CVE-2009-1955, CVE-2009-1956 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   libaprutil1                     1.2.12+dfsg-3ubuntu0.1  Ubuntu 8.10:   libaprutil1                     1.2.12+dfsg-7ubuntu0.1  Ubuntu 9.04:   libaprutil1                     1.2.12+dfsg-8ubuntu0.1  After a standard system upgrade you need to restart any services that use apr-util, such as Apache or svnserve, to effect the necessary changes.  Details follow:  Matthew Palmer discovered an underflow flaw in apr-util. An attacker could cause a denial of service via application crash in Apache using a crafted SVNMasterURI directive, .htaccess file, or when using mod_apreq2. Applications using libapreq2 are also affected. (CVE-2009-0023)  It was discovered that the XML parser did not properly handle entity expansion. A remote attacker could cause a denial of service via memory resource consumption by sending a crafted request to an Apache server configured to use mod_dav or mod_dav_svn. (CVE-2009-1955)  C. Michael Pilato discovered an off-by-one buffer overflow in apr-util when formatting certain strings. For big-endian machines (powerpc, hppa and sparc in Ubuntu), a remote attacker could cause a denial of service or information disclosure leak. All other architectures for Ubuntu are not considered to be at risk. (CVE-2009-1956) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-786-1)

---

