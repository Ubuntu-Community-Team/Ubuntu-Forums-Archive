---
title: "USN-822-1: KDE-Libs vulnerabilities"
date: 2009-08-24
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-08-24
Referenced CVEs: 
                                       CVE-2009-0945, CVE-2009-1687, CVE-2009-1690, CVE-2009-1698        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-822-1            August 24, 2009 kde4libs, kdelibs vulnerabilities CVE-2009-0945, CVE-2009-1687, CVE-2009-1690, CVE-2009-1698 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   kdelibs4c2a                     4:3.5.10-0ubuntu1~hardy1.2  Ubuntu 8.10:   kdelibs4c2a                     4:3.5.10-0ubuntu6.1   kdelibs5                        4:4.1.4-0ubuntu1~intrepid1.2  Ubuntu 9.04:   kdelibs4c2a                     4:3.5.10.dfsg.1-1ubuntu8.1   kdelibs5                        4:4.2.2-0ubuntu5.1  After a standard system upgrade you need to restart your session to effect the necessary changes.  Details follow:  It was discovered that KDE-Libs did not properly handle certain malformed SVG images. If a user were tricked into opening a specially crafted SVG image, an attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. This issue only affected Ubuntu 9.04. (CVE-2009-0945)  It was discovered that the KDE JavaScript garbage collector did not properly handle memory allocation failures. If a user were tricked into viewing a malicious website, an attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-1687)  It was discovered that KDE-Libs did not properly handle HTML content in the head element. If a user were tricked into viewing a malicious website, an attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-1690)  It was discovered that KDE-Libs did not properly handle the Cascading Style Sheets (CSS) attr function call. If a user were tricked into viewing a malicious website, an attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-1698)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-822-1)

---

