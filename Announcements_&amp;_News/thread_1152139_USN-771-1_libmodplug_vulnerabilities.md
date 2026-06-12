---
title: "USN-771-1: libmodplug vulnerabilities"
date: 2009-05-07
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-05-07
Referenced CVEs: 
                                       CVE-2009-1438, CVE-2009-1513        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-771-1               May 07, 2009 libmodplug vulnerabilities CVE-2009-1438, CVE-2009-1513 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libmodplug0c2                   1:0.7-5ubuntu0.6.06.2  Ubuntu 8.04 LTS:   libmodplug0c2                   1:0.7-7ubuntu0.8.04.1  Ubuntu 8.10:   libmodplug0c2                   1:0.7-7ubuntu0.8.10.1  Ubuntu 9.04:   libmodplug0c2                   1:0.8.4-3ubuntu1.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that libmodplug did not correctly handle certain parameters when parsing MED media files. If a user or automated system were tricked into opening a crafted MED file, an attacker could execute arbitrary code with privileges of the user invoking the program. (CVE-2009-1438)  Manfred Tremmel and Stanislav Brabec discovered that libmodplug did not correctly handle long instrument names when parsing PAT sample files. If a user or automated system were tricked into opening a crafted PAT file, an attacker could cause a denial of service or execute arbitrary code with privileges of the user invoking the program. This issue only affected Ubuntu 9.04. (CVE-2009-1438)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-771-1)

---

