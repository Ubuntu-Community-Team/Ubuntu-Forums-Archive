---
title: "USN-662-1: Linux kernel vulnerabilities"
date: 2008-11-05
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-11-05
Referenced CVEs: 
CVE-2008-3528, CVE-2008-4395


Description: 
===========================================================Ubuntu Security Notice USN-662-1          November 05, 2008linux vulnerabilityCVE-2008-3528, CVE-2008-4395===========================================================A security issue affects the following Ubuntu releases:Ubuntu 8.10This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 8.10:  linux-image-2.6.27-7-generic    2.6.27-7.16  linux-image-2.6.27-7-server     2.6.27-7.16  linux-image-2.6.27-7-virtual    2.6.27-7.16After a standard system upgrade you need to reboot your computer toeffect the necessary changes.Details follow:It was discovered that the Linux kernel could be made to hang temporarilywhen mounting corrupted ext2/3 filesystems.  If a user were tricked intomounting a specially crafted filesystem, a remote attacker could causesystem hangs, leading to a denial of service. (CVE-2008-3528)Anders Kaseorg discovered that ndiswrapper did not correctly handle longESSIDs.  For a system using ndiswrapper, a physically near-by attackercould generate specially crafted wireless network traffic and executearbitrary code with root privileges. (CVE-2008-4395)





[More...](http://www.ubuntu.com/usn/usn-662-1)

---

