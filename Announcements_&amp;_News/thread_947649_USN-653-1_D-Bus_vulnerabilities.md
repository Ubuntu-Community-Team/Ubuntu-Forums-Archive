---
title: "USN-653-1: D-Bus vulnerabilities"
date: 2008-10-14
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-10-14
Referenced CVEs: 
CVE-2008-0595, CVE-2008-3834


Description: 
 =========================================================== Ubuntu Security Notice USN-653-1           October 14, 2008 dbus vulnerabilities CVE-2008-0595, CVE-2008-3834 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libdbus-1-2                     0.60-6ubuntu8.3  Ubuntu 7.04:   libdbus-1-3                     1.0.2-1ubuntu4.2  Ubuntu 7.10:   libdbus-1-3                     1.1.1-3ubuntu4.2  Ubuntu 8.04 LTS:   libdbus-1-3                     1.1.20-1ubuntu3.1  After a standard system upgrade you need to reboot your computer to effect the necessary changes.  Details follow:  Havoc Pennington discovered that the D-Bus daemon did not correctly validate certain security policies.  If a local user sent a specially crafted D-Bus request, they could bypass security policies that had a "send_interface" defined. (CVE-2008-0595)  It was discovered that the D-Bus library did not correctly validate certain corrupted signatures.  If a local user sent a specially crafted D-Bus request, they could crash applications linked against the D-Bus library, leading to a denial of service. (CVE-2008-3834) 





[More...](http://www.ubuntu.com/usn/usn-653-1)

---

