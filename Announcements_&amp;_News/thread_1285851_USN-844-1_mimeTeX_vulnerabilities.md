---
title: "USN-844-1: mimeTeX vulnerabilities"
date: 2009-10-08
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-10-08
Referenced CVEs: 
                                       CVE-2009-1382, CVE-2009-2459        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-844-1           October 08, 2009 mimetex vulnerabilities CVE-2009-1382, CVE-2009-2459 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   mimetex                         1.50-1ubuntu0.8.04.1  Ubuntu 8.10:   mimetex                         1.50-1ubuntu0.8.10.1  Ubuntu 9.04:   mimetex                         1.50-1ubuntu0.9.04.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Chris Evans discovered that mimeTeX incorrectly handled certain long tags. An attacker could exploit this with a crafted mimeTeX expression and cause a denial of service or possibly execute arbitrary code. (CVE-2009-1382)  Chris Evans discovered that mimeTeX contained certain directives that may be unsuitable for handling untrusted user input. This update fixed the issue by disabling the \input and \counter tags. (CVE-2009-2459)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-844-1)

---

