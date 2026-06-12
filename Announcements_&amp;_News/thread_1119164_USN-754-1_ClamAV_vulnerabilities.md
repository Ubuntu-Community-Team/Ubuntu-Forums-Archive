---
title: "USN-754-1: ClamAV vulnerabilities"
date: 2009-04-07
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-04-07
Description: 
                                        =========================================================== Ubuntu Security Notice USN-754-1             April 07, 2009 clamav vulnerabilities [https://launchpad.net/bugs/354190](https://launchpad.net/bugs/354190) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.10:   libclamav5                      0.94.dfsg.2-1ubuntu0.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that ClamAV did not properly verify its input when processing TAR archives. A remote attacker could send a specially crafted TAR file and cause a denial of service via infinite loop.  It was discovered that ClamAV did not properly validate Portable Executable (PE) files. A remote attacker could send a crafted PE file and cause a denial of service (divide by zero). 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-754-1)

---

