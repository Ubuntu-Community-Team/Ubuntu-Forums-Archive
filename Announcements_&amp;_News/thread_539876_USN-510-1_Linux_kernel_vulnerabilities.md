---
title: "USN-510-1: Linux kernel vulnerabilities"
date: 2007-08-31
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-08-31
Referenced CVEs:
CVE-2007-2525, CVE-2007-2875, CVE-2007-2876, CVE-2007-2878, CVE-2007-3104, CVE-2007-3105, CVE-2007-3513, CVE-2007-3642, CVE-2007-3843, CVE-2007-3848, CVE-2007-3851, CVE-2007-4308


Description:
 ===========================================================  Ubuntu Security Notice USN-510-1            August 31, 2007 linux-source-2.6.20 vulnerabilities CVE-2007-2525, CVE-2007-2875, CVE-2007-2876, CVE-2007-2878, CVE-2007-3104, CVE-2007-3105, CVE-2007-3513, CVE-2007-3642, CVE-2007-3843, CVE-2007-3848, CVE-2007-3851, CVE-2007-4308 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 7.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 7.04:   linux-image-2.6.20-16-386                    2.6.20-16.31   linux-image-2.6.20-16-generic                2.6.20-16.31   linux-image-2.6.20-16-hppa32                 2.6.20-16.31   linux-image-2.6.20-16-hppa64                 2.6.20-16.31   linux-image-2.6.20-16-itanium                2.6.20-16.31   linux-image-2.6.20-16-lowlatency             2.6.20-16.31   linux-image-2.6.20-16-mckinley               2.6.20-16.31   linux-image-2.6.20-16-powerpc                2.6.20-16.31   linux-image-2.6.20-16-powerpc-smp            2.6.20-16.31   linux-image-2.6.20-16-powerpc64-smp          2.6.20-16.31   linux-image-2.6.20-16-server                 2.6.20-16.31   linux-image-2.6.20-16-server-bigiron         2.6.20-16.31   linux-image-2.6.20-16-sparc64                2.6.20-16.31   linux-image-2.6.20-16-sparc64-smp            2.6.20-16.31  After a standard system upgrade you need to reboot your computer to affect the necessary changes.  Details follow:  A flaw was discovered in the PPP over Ethernet implementation.  Local attackers could manipulate ioctls and cause kernel memory consumption leading to a denial of service. (CVE-2007-2525)  An integer underflow was discovered in the cpuset filesystem.  If mounted, local attackers could obtain kernel memory using large file offsets while reading the tasks file. This could disclose sensitive data. (CVE-2007-2875)  Vilmos Nebehaj discovered that the SCTP netfilter code did not correctly validate certain states.  A remote attacker could send a specially crafted packet causing a denial of service. (CVE-2007-2876)  Luca Tettamanti discovered a flaw in the VFAT compat ioctls on 64-bit systems.  A local attacker could corrupt a kernel_dirent struct and cause a denial of service. (CVE-2007-2878)  A flaw in the sysfs_readdir function allowed a local user to cause a denial of service by dereferencing a NULL pointer. (CVE-2007-3104)  A buffer overflow was discovered in the random number generator.  In environments with granular assignment of root privileges, a local attacker could gain additional privileges. (CVE-2007-3105)  A flaw was discovered in the usblcd driver.  A local attacker could cause large amounts of kernel memory consumption, leading to a denial of service. (CVE-2007-3513)  Zhongling Wen discovered that the h323 conntrack handler did not correctly handle certain bitfields.  A remote attacker could send a specially crafted packet and cause a denial of service. (CVE-2007-3642)  A flaw was discovered in the CIFS mount security checking.  Remote attackers could spoof CIFS network traffic, which could lead a client to trust the connection. (CVE-2007-3843)  It was discovered that certain setuid-root processes did not correctly reset process death signal handlers.  A local user could manipulate this to send signals to processes they would not normally have access to. (CVE-2007-3848)  The Direct Rendering Manager for the i915 driver could be made to write to arbitrary memory locations.  An attacker with access to a running X11 session could send a specially crafted buffer and gain root privileges. (CVE-2007-3851)  It was discovered that the aacraid SCSI driver did not correctly check permissions on certain ioctls.  A local attacker could cause a denial of service or gain privileges. (CVE-2007-4308) 





[More...](http://www.ubuntu.com/usn/usn-510-1)

---

