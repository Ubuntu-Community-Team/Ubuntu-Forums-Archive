---
title: "USN-836-1: WebKit vulnerabilities"
date: 2009-09-23
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-09-23
Referenced CVEs: 
                                       CVE-2009-0945, CVE-2009-1687, CVE-2009-1690, CVE-2009-1698, CVE-2009-1711, CVE-2009-1712, CVE-2009-1725        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-836-1         September 23, 2009 webkit vulnerabilities CVE-2009-0945, CVE-2009-1687, CVE-2009-1690, CVE-2009-1698, CVE-2009-1711, CVE-2009-1712, CVE-2009-1725 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.10:   libwebkit-1.0-1                 1.0.1-2ubuntu0.2   libwebkit-1.0-1-dbg             1.0.1-2ubuntu0.2   libwebkit-dev                   1.0.1-2ubuntu0.2  Ubuntu 9.04:   libwebkit-1.0-1                 1.0.1-4ubuntu0.1   libwebkit-1.0-1-dbg             1.0.1-4ubuntu0.1   libwebkit-dev                   1.0.1-4ubuntu0.1  After a standard system upgrade you need to restart any applications that use WebKit, such as Epiphany-webkit and Midori, to effect the necessary changes.  Details follow:  It was discovered that WebKit did not properly handle certain SVGPathList data structures. If a user were tricked into viewing a malicious website, an attacker could exploit this to execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-0945)  Several flaws were discovered in the WebKit browser and JavaScript engines. If a user were tricked into viewing a malicious website, a remote attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-1687, CVE-2009-1690, CVE-2009-1698, CVE-2009-1711, CVE-2009-1725)  It was discovered that WebKit did not prevent the loading of local Java applets. If a user were tricked into viewing a malicious website, an attacker could exploit this to execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-1712)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-836-1)

---

