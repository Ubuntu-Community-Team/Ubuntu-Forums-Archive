---
title: "USN-849-1: libsndfile vulnerabilities"
date: 2009-10-15
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-10-15
Referenced CVEs: 
                                       CVE-2009-1788, CVE-2009-1791        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-849-1           October 15, 2009 libsndfile vulnerabilities CVE-2009-1788, CVE-2009-1791 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   libsndfile1                     1.0.17-4ubuntu0.8.04.2  Ubuntu 8.10:   libsndfile1                     1.0.17-4ubuntu0.8.10.2  Ubuntu 9.04:   libsndfile1                     1.0.17-4ubuntu1.1  After a standard system upgrade you need to restart your session to effect the necessary changes.  Details follow:  Tobias Klein discovered a heap-based buffer overflow in libsndfile. If a user or automated system processed a crafted VOC file, an attacker could cause a denial of service via application crash, or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-1788)  Erik de Castro Lopo discovered a similar heap-based buffer overflow when processing AIFF files. If a user or automated system processed a crafted AIFF file, an attacker could cause a denial of service via application crash, or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-1791) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-849-1)

---

