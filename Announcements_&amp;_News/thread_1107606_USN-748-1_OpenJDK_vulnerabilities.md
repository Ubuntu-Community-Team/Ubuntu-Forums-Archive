---
title: "USN-748-1: OpenJDK vulnerabilities"
date: 2009-03-26
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-03-26
Referenced CVEs: 
                                       CVE-2006-2426, CVE-2009-1093, CVE-2009-1094, CVE-2009-1095, CVE-2009-1096, CVE-2009-1097, CVE-2009-1098, CVE-2009-1100, CVE-2009-1101, CVE-2009-1102        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-748-1             March 26, 2009 openjdk-6 vulnerabilities CVE-2006-2426, CVE-2009-1093, CVE-2009-1094, CVE-2009-1095, CVE-2009-1096, CVE-2009-1097, CVE-2009-1098, CVE-2009-1100, CVE-2009-1101, CVE-2009-1102 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.10:   icedtea6-plugin                 6b12-0ubuntu6.4   openjdk-6-jdk                   6b12-0ubuntu6.4   openjdk-6-jre                   6b12-0ubuntu6.4   openjdk-6-jre-headless          6b12-0ubuntu6.4   openjdk-6-jre-lib               6b12-0ubuntu6.4  After a standard system upgrade you need to restart any Java applications to effect the necessary changes.  Details follow:  It was discovered that font creation could leak temporary files. If a user were tricked into loading a malicious program or applet, a remote attacker could consume disk space, leading to a denial of service. (CVE-2006-2426, CVE-2009-1100)  It was discovered that the lightweight HttpServer did not correctly close files on dataless connections.  A remote attacker could send specially crafted requests, leading to a denial of service. (CVE-2009-1101)  Certain 64bit Java actions would crash an application.  A local attacker might be able to cause a denial of service. (CVE-2009-1102)  It was discovered that LDAP connections did not close correctly. A remote attacker could send specially crafted requests, leading to a denial of service.  (CVE-2009-1093)  Java LDAP routines did not unserialize certain data correctly.  A remote attacker could send specially crafted requests that could lead to arbitrary code execution. (CVE-2009-1094)  Java did not correctly check certain JAR headers.  If a user or automated system were tricked into processing a malicious JAR file, a remote attacker could crash the application, leading to a denial of service. (CVE-2009-1095, CVE-2009-1096)  It was discovered that PNG and GIF decoding in Java could lead to memory corruption.  If a user or automated system were tricked into processing a specially crafted image, a remote attacker could crash the application, leading to a denial of service. (CVE-2009-1097, CVE-2009-1098) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-748-1)

---

