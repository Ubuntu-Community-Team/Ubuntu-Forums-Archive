---
title: "USN-543-1: VMWare vulnerabilities"
date: 2007-11-15
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-11-15
Referenced CVEs:
CVE-2007-0061, CVE-2007-0062, CVE-2007-0063, CVE-2007-4496, CVE-2007-4497


Description:
 ===========================================================  Ubuntu Security Notice USN-543-1          November 15, 2007 linux-restricted-modules-2.6.17/20, vmware-player-kernel-2.6.15 vulnerabilities CVE-2007-0061, CVE-2007-0062, CVE-2007-0063, CVE-2007-4496, CVE-2007-4497 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   vmware-player-kernel-modules-2.6.15-29  2.6.15.11-13  Ubuntu 6.10:   vmware-player-kernel-modules-2.6.17-12  2.6.17.9-12.4  Ubuntu 7.04:   vmware-player-kernel-modules-2.6.20-16  2.6.20.6-16.30   vmware-server-kernel-modules-2.6.20-16  2.6.20.6-16.30   vmware-tools-kernel-modules-2.6.20-16  2.6.20.6-16.30  After a standard system upgrade you need to reboot your computer to effect the necessary changes.  Details follow:  Neel Mehta and Ryan Smith discovered that the VMWare Player DHCP server did not correctly handle certain packet structures.  Remote attackers could send specially crafted packets and gain root privileges. (CVE-2007-0061, CVE-2007-0062, CVE-2007-0063)  Rafal Wojtczvk discovered multiple memory corruption issues in VMWare Player.  Attackers with administrative privileges in a guest operating system could cause a denial of service or possibly execute arbitrary code on the host operating system.  (CVE-2007-4496, CVE-2007-4497) 





[More...](http://www.ubuntu.com/usn/usn-543-1)

---

