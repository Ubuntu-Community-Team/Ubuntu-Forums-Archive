---
title: "USN-547-1: PCRE vulnerabilities"
date: 2007-11-27
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-11-27
Referenced CVEs:
CVE-2007-1659, CVE-2007-1660, CVE-2007-1661, CVE-2007-1662, CVE-2007-4766, CVE-2007-4767, CVE-2007-4768


Description:
 ===========================================================  Ubuntu Security Notice USN-547-1          November 27, 2007 pcre3 vulnerabilities CVE-2007-1659, CVE-2007-1660, CVE-2007-1661, CVE-2007-1662, CVE-2007-4766, CVE-2007-4767, CVE-2007-4768 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libpcre3                        7.4-0ubuntu0.6.06.1   libpcrecpp0                     7.4-0ubuntu0.6.06.1  Ubuntu 6.10:   libpcre3                        7.4-0ubuntu0.6.10.1   libpcrecpp0                     7.4-0ubuntu0.6.10.1  Ubuntu 7.04:   libpcre3                        7.4-0ubuntu0.7.04.1   libpcrecpp0                     7.4-0ubuntu0.7.04.1  Ubuntu 7.10:   libpcre3                        7.4-0ubuntu0.7.10.1   libpcrecpp0                     7.4-0ubuntu0.7.10.1  After a standard system upgrade you need to reboot your computer to effect the necessary changes.  Due to the large internal code changes needed to solve outstanding flaws, it was not possible to backport all the upstream security fixes to the earlier released versions.  To address this, the pcre3 library has been updated to the latest stable release (7.4), which includes fixes for all known security issues.  While the new version is ABI compatible, efforts have been taken to maintain behavioral compatibility with the earlier versions.  Details follow:  Tavis Ormandy and Will Drewry discovered multiple flaws in the regular expression handling of PCRE.  By tricking a user or service into running specially crafted expressions via applications linked against libpcre3, a remote attacker could crash the application, monopolize CPU resources, or possibly execute arbitrary code with the application's privileges. 





[More...](http://www.ubuntu.com/usn/usn-547-1)

---

