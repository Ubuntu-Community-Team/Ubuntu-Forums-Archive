---
title: "USN-815-1: libxml2 vulnerabilities"
date: 2009-08-11
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-08-11
Referenced CVEs: 
                                       CVE-2008-3529, CVE-2009-2414, CVE-2009-2416        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-815-1            August 11, 2009 libxml2 vulnerabilities CVE-2008-3529, CVE-2009-2414, CVE-2009-2416 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libxml2                         2.6.24.dfsg-1ubuntu1.5  Ubuntu 8.04 LTS:   libxml2                         2.6.31.dfsg-2ubuntu1.4  Ubuntu 8.10:   libxml2                         2.6.32.dfsg-4ubuntu1.2  Ubuntu 9.04:   libxml2                         2.6.32.dfsg-5ubuntu4.2  After a standard system upgrade you need to restart your sessions to effect the necessary changes.  Details follow:  It was discovered that libxml2 did not correctly handle root XML document element DTD definitions. If a user were tricked into processing a specially crafted XML document, a remote attacker could cause the application linked against libxml2 to crash, leading to a denial of service. (CVE-2009-2414)  It was discovered that libxml2 did not correctly parse Notation and Enumeration attribute types. If a user were tricked into processing a specially crafted XML document, a remote attacker could cause the application linked against libxml2 to crash, leading to a denial of service. (CVE-2009-2416)  USN-644-1 fixed a vulnerability in libxml2. This advisory provides the corresponding update for Ubuntu 9.04.  Original advisory details:   It was discovered that libxml2 did not correctly handle long entity names.  If a user were tricked into processing a specially crafted XML document, a  remote attacker could execute arbitrary code with user privileges or cause  the application linked against libxml2 to crash, leading to a denial of  service. (CVE-2008-3529)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-815-1)

---

