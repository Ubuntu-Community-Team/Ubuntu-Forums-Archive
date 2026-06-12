---
title: "USN-633-1: libxslt vulnerabilities"
date: 2008-08-01
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-08-01
Referenced CVEs: 
CVE-2008-1767, CVE-2008-2935


Description: 
 ===========================================================  Ubuntu Security Notice USN-633-1            August 01, 2008 libxslt vulnerabilities CVE-2008-1767, CVE-2008-2935 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libxslt1.1                      1.1.15-1ubuntu1.2  Ubuntu 7.04:   libxslt1.1                      1.1.20-0ubuntu2.2  Ubuntu 7.10:   libxslt1.1                      1.1.21-2ubuntu2.2  Ubuntu 8.04 LTS:   libxslt1.1                      1.1.22-1ubuntu1.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that long transformation matches in libxslt could overflow.  If an attacker were able to make an application linked against libxslt process malicious XSL style sheet input, they could execute arbitrary code with user privileges or cause the application to crash, leading to a denial of serivce. (CVE-2008-1767)  Chris Evans discovered that the RC4 processing code in libxslt did not correctly handle corrupted key information.  If a remote attacker were able to make an application linked against libxslt process malicious XML input, they could crash the application, leading to a denial of service. (CVE-2008-2935) 





[More...](http://www.ubuntu.com/usn/usn-633-1)

---

