---
title: "USN-730-1: libpng vulnerabilities"
date: 2009-03-06
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-03-06
Referenced CVEs: 
CVE-2007-5268, CVE-2007-5269, CVE-2008-1382, CVE-2008-3964, CVE-2008-5907, CVE-2009-0040


Description: 
 =========================================================== Ubuntu Security Notice USN-730-1             March 06, 2009 libpng vulnerabilities CVE-2007-5268, CVE-2007-5269, CVE-2008-1382, CVE-2008-3964, CVE-2008-5907, CVE-2009-0040 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libpng12-0                      1.2.8rel-5ubuntu0.4  Ubuntu 7.10:   libpng12-0                      1.2.15~beta5-2ubuntu0.2  Ubuntu 8.04 LTS:   libpng12-0                      1.2.15~beta5-3ubuntu0.1  Ubuntu 8.10:   libpng12-0                      1.2.27-1ubuntu0.1  After a standard system upgrade you need to reboot your computer to effect the necessary changes.  Details follow:  It was discovered that libpng did not properly perform bounds checking in certain operations. An attacker could send a specially crafted PNG image and cause a denial of service in applications linked against libpng. This issue only affected Ubuntu 8.04 LTS. (CVE-2007-5268, CVE-2007-5269)  Tavis Ormandy discovered that libpng did not properly initialize memory. If a user or automated system were tricked into opening a crafted PNG image, an attacker could cause a denial of service via application crash, or possibly execute arbitrary code with the privileges of the user invoking the program. This issue did not affect Ubuntu 8.10. (CVE-2008-1382)  Harald van Dijk discovered an off-by-one error in libpng. An attacker could could cause an application crash in programs using pngtest. (CVE-2008-3964)  It was discovered that libpng did not properly NULL terminate a keyword string. An attacker could exploit this to set arbitrary memory locations to zero. (CVE-2008-5907)  Glenn Randers-Pehrson discovered that libpng did not properly initialize pointers. If a user or automated system were tricked into opening a crafted PNG file, an attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-0040) 





[More...](http://www.ubuntu.com/usn/usn-730-1)

---

