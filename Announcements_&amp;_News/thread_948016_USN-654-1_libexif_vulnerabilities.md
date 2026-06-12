---
title: "USN-654-1: libexif vulnerabilities"
date: 2008-10-14
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-10-14
Referenced CVEs: 
CVE-2007-6351, CVE-2007-6352


Description: 
 =========================================================== Ubuntu Security Notice USN-654-1           October 14, 2008 libexif vulnerabilities CVE-2007-6351, CVE-2007-6352 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libexif12                       0.6.12-2ubuntu0.3  Ubuntu 7.04:   libexif12                       0.6.13-5ubuntu0.3  Ubuntu 7.10:   libexif12                       0.6.16-1ubuntu0.1  After a standard system upgrade you need to restart your session to effect the necessary changes.  Details follow:  Meder Kydyraliev discovered that libexif did not correctly handle certain EXIF headers.  If a user or automated system were tricked into processing a specially crafted image, a remote attacker could cause the application linked against libexif to crash, leading to a denial of service, or possibly executing arbitrary code with user privileges. 





[More...](http://www.ubuntu.com/usn/usn-654-1)

---

