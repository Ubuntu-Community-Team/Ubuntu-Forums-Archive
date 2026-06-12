---
title: "USN-499-1: Apache vulnerabilities"
date: 2007-08-17
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-08-17
Referenced CVEs:
CVE-2006-5752, CVE-2007-1863, CVE-2007-3304


Description:
 ===========================================================  Ubuntu Security Notice USN-499-1            August 16, 2007 apache2 vulnerabilities CVE-2006-5752, CVE-2007-1863, CVE-2007-3304 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   apache2-common                           2.0.55-4ubuntu2.2   apache2-mpm-prefork                      2.0.55-4ubuntu2.2   apache2-mpm-worker                       2.0.55-4ubuntu2.2  Ubuntu 6.10:   apache2-common                           2.0.55-4ubuntu4.1   apache2-mpm-prefork                      2.0.55-4ubuntu4.1   apache2-mpm-worker                       2.0.55-4ubuntu4.1  Ubuntu 7.04:   apache2-mpm-prefork                      2.2.3-3.2ubuntu0.1   apache2-mpm-worker                       2.2.3-3.2ubuntu0.1   apache2.2-common                         2.2.3-3.2ubuntu0.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Stefan Esser discovered that mod_status did not force a character set, which could result in browsers becoming vulnerable to XSS attacks when processing the output.  If a user were tricked into viewing server status output during a crafted server request, a remote attacker could exploit this to modify the contents, or steal confidential data (such as passwords), within the same domain.  By default, mod_status is disabled in Ubuntu. (CVE-2006-5752)  Niklas Edmundsson discovered that the mod_cache module could be made to crash using a specially crafted request.  A remote user could use this to cause a denial of service if Apache was configured to use a threaded worker.  By default, mod_cache is disabled in Ubuntu. (CVE-2007-1863)  A flaw was discovered in the signal handling of Apache.  A local attacker could trick Apache into sending SIGUSR1 to other processes. The vulnerable code was only present in Ubuntu Feisty. (CVE-2007-3304) 





[More...](http://www.ubuntu.com/usn/usn-499-1)

---

