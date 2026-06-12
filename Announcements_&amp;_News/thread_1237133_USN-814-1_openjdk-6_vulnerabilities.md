---
title: "USN-814-1: openjdk-6 vulnerabilities"
date: 2009-08-11
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-08-11
Referenced CVEs: 
                                       CVE-2009-0217, CVE-2009-2475, CVE-2009-2476, CVE-2009-2625, CVE-2009-2670, CVE-2009-2671, CVE-2009-2672, CVE-2009-2673, CVE-2009-2674, CVE-2009-2675, CVE-2009-2676, CVE-2009-2690        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-814-1            August 11, 2009 openjdk-6 vulnerabilities CVE-2009-0217, CVE-2009-2475, CVE-2009-2476, CVE-2009-2625, CVE-2009-2670, CVE-2009-2671, CVE-2009-2672, CVE-2009-2673, CVE-2009-2674, CVE-2009-2675, CVE-2009-2676, CVE-2009-2690 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.10:   icedtea6-plugin                 6b12-0ubuntu6.5   openjdk-6-jre                   6b12-0ubuntu6.5   openjdk-6-jre-lib               6b12-0ubuntu6.5  Ubuntu 9.04:   icedtea6-plugin                 6b14-1.4.1-0ubuntu11   openjdk-6-jre                   6b14-1.4.1-0ubuntu11   openjdk-6-jre-lib               6b14-1.4.1-0ubuntu11  After a standard system upgrade you need to restart any Java applications to effect the necessary changes.  Details follow:  It was discovered that the XML HMAC signature system did not correctly check certain lengths.  If an attacker sent a truncated HMAC, it could bypass authentication, leading to potential privilege escalation. (CVE-2009-0217)  It was discovered that certain variables could leak information.  If a user were tricked into running a malicious Java applet, a remote attacker could exploit this gain access to private information and potentially run untrusted code. (CVE-2009-2475, CVE-2009-2690)  A flaw was discovered the OpenType checking.  If a user were tricked into running a malicious Java applet, a remote attacker could bypass access restrictions. (CVE-2009-2476)  It was discovered that the XML processor did not correctly check recursion.  If a user or automated system were tricked into processing a specially crafted XML, the system could crash, leading to a denial of service. (CVE-2009-2625)  It was discovered that the Java audio subsystem did not correctly validate certain parameters.  If a user were tricked into running an untrusted applet, a remote attacker could read system properties.  (CVE-2009-2670)  Multiple flaws were discovered in the proxy subsystem.  If a user were tricked into running an untrusted applet, a remote attacker could discover local user names, obtain access to sensitive information, or bypass socket restrictions, leading to a loss of privacy. (CVE-2009-2671, CVE-2009-2672, CVE-2009-2673)  Flaws were discovered in the handling of JPEG images, Unpack200 archives, and JDK13Services.  If a user were tricked into running an untrusted applet, a remote attacker could load a specially crafted file that would bypass local file access protections and run arbitrary code with user privileges. (CVE-2009-2674, CVE-2009-2675, CVE-2009-2676, CVE-2009-2689) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-814-1)

---

