---
title: "USN-682-1: libvorbis vulnerabilities"
date: 2008-12-01
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-12-01
Referenced CVEs: 
CVE-2008-1419, CVE-2008-1420, CVE-2008-1423


Description: 
===========================================================Ubuntu Security Notice USN-682-1          December 01, 2008libvorbis vulnerabilitiesCVE-2008-1419, CVE-2008-1420, CVE-2008-1423===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSUbuntu 7.10Ubuntu 8.04 LTSThis advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  libvorbis0a                     1.1.2-0ubuntu2.3Ubuntu 7.10:  libvorbis0a                     1.2.0.dfsg-1ubuntu0.1Ubuntu 8.04 LTS:  libvorbis0a                     1.2.0.dfsg-2ubuntu0.1After a standard system upgrade you need to restart any applications thatuse libvorbis, such as Totem and gtkpod, to effect the necessary changes.Details follow:It was discovered that libvorbis did not correctly handle certain malformedsound files. If a user were tricked into opening a specially crafted soundfile with an application that uses libvorbis, an attacker could executearbitrary code with the user's privileges.





[More...](http://www.ubuntu.com/usn/USN-682-1)

---

