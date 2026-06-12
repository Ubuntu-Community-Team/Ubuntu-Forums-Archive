---
title: "USN-831-1: OpenEXR vulnerabilities"
date: 2009-09-14
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-09-14
Referenced CVEs: 
                                       CVE-2009-1720, CVE-2009-1721, CVE-2009-1722        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-831-1         September 14, 2009 openexr vulnerabilities CVE-2009-1720, CVE-2009-1721, CVE-2009-1722 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   libopenexr2ldbl                 1.2.2-4.4ubuntu1.1  Ubuntu 8.10:   libopenexr6                     1.6.1-3ubuntu1.8.10.1  Ubuntu 9.04:   libopenexr6                     1.6.1-3ubuntu1.9.04.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Drew Yao discovered several flaws in the way OpenEXR handled certain malformed EXR image files. If a user were tricked into opening a crafted EXR image file, an attacker could cause a denial of service via application crash, or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-1720, CVE-2009-1721)  It was discovered that OpenEXR did not properly handle certain malformed EXR image files. If a user were tricked into opening a crafted EXR image file, an attacker could cause a denial of service via application crash, or possibly execute arbitrary code with the privileges of the user invoking the program. This issue only affected Ubuntu 8.04 LTS. (CVE-2009-1722)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-831-1)

---

