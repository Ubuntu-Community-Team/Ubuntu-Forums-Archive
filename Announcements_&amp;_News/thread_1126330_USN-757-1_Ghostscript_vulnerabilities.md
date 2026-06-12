---
title: "USN-757-1: Ghostscript vulnerabilities"
date: 2009-04-15
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-04-15
Referenced CVEs: 
                                       CVE-2007-6725, CVE-2008-6679, CVE-2009-0196, CVE-2009-0583, CVE-2009-0584, CVE-2009-0792        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-757-1             April 15, 2009 ghostscript, gs-esp, gs-gpl vulnerabilities CVE-2007-6725, CVE-2008-6679, CVE-2009-0196, CVE-2009-0583, CVE-2009-0584, CVE-2009-0792 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   gs-esp                          8.15.2.dfsg.0ubuntu1-0ubuntu1.2   gs-gpl                          8.15-4ubuntu3.3  Ubuntu 8.04 LTS:   libgs8                          8.61.dfsg.1-1ubuntu3.2  Ubuntu 8.10:   libgs8                          8.63.dfsg.1-0ubuntu6.4  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that Ghostscript contained a buffer underflow in its CCITTFax decoding filter. If a user or automated system were tricked into opening a crafted PDF file, an attacker could cause a denial of service or execute arbitrary code with privileges of the user invoking the program. (CVE-2007-6725)  It was discovered that Ghostscript contained a buffer overflow in the BaseFont writer module. If a user or automated system were tricked into opening a crafted Postscript file, an attacker could cause a denial of service or execute arbitrary code with privileges of the user invoking the program. (CVE-2008-6679)  It was discovered that Ghostscript contained additional integer overflows in its ICC color management library. If a user or automated system were tricked into opening a crafted Postscript or PDF file, an attacker could cause a denial of service or execute arbitrary code with privileges of the user invoking the program. (CVE-2009-0792)  Alin Rad Pop discovered that Ghostscript contained a buffer overflow in the jbig2dec library. If a user or automated system were tricked into opening a crafted PDF file, an attacker could cause a denial of service or execute arbitrary code with privileges of the user invoking the program. (CVE-2009-0196)  USN-743-1 provided updated ghostscript and gs-gpl packages to fix two security vulnerabilities. This update corrects the same vulnerabilities in the gs-esp package.  Original advisory details:  It was discovered that Ghostscript contained multiple integer overflows in  its ICC color management library. If a user or automated system were  tricked into opening a crafted Postscript file, an attacker could cause a  denial of service or execute arbitrary code with privileges of the user  invoking the program. (CVE-2009-0583)   It was discovered that Ghostscript did not properly perform bounds  checking in its ICC color management library. If a user or automated  system were tricked into opening a crafted Postscript file, an attacker  could cause a denial of service or execute arbitrary code with privileges  of the user invoking the program. (CVE-2009-0584)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-757-1)

---

