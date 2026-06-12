---
title: "USN-509-1: Linux kernel vulnerabilities"
date: 2007-08-31
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-08-31
Referenced CVEs:
CVE-2007-3104, CVE-2007-3105, CVE-2007-3513, CVE-2007-3848, CVE-2007-3851, CVE-2007-4308


Description:
 ===========================================================  Ubuntu Security Notice USN-509-1            August 31, 2007 linux-source-2.6.17 vulnerabilities CVE-2007-3104, CVE-2007-3105, CVE-2007-3513, CVE-2007-3848, CVE-2007-3851, CVE-2007-4308 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.10:   linux-image-2.6.17-12-386                  2.6.17.1-12.40   linux-image-2.6.17-12-generic              2.6.17.1-12.40   linux-image-2.6.17-12-hppa32               2.6.17.1-12.40   linux-image-2.6.17-12-hppa64               2.6.17.1-12.40   linux-image-2.6.17-12-itanium              2.6.17.1-12.40   linux-image-2.6.17-12-mckinley             2.6.17.1-12.40   linux-image-2.6.17-12-powerpc              2.6.17.1-12.40   linux-image-2.6.17-12-powerpc-smp          2.6.17.1-12.40   linux-image-2.6.17-12-powerpc64-smp        2.6.17.1-12.40   linux-image-2.6.17-12-server               2.6.17.1-12.40   linux-image-2.6.17-12-server-bigiron       2.6.17.1-12.40   linux-image-2.6.17-12-sparc64              2.6.17.1-12.40   linux-image-2.6.17-12-sparc64-smp          2.6.17.1-12.40  After a standard system upgrade you need to reboot your computer to effect the necessary changes.  Details follow:  A flaw in the sysfs_readdir function allowed a local user to cause a denial of service by dereferencing a NULL pointer. (CVE-2007-3104)  A buffer overflow was discovered in the random number generator.  In environments with granular assignment of root privileges, a local attacker could gain additional privileges. (CVE-2007-3105)  A flaw was discovered in the usblcd driver.  A local attacker could cause large amounts of kernel memory consumption, leading to a denial of service. (CVE-2007-3513)  It was discovered that certain setuid-root processes did not correctly reset process death signal handlers.  A local user could manipulate this to send signals to processes they would not normally have access to. (CVE-2007-3848)  The Direct Rendering Manager for the i915 driver could be made to write to arbitrary memory locations.  An attacker with access to a running X11 session could send a specially crafted buffer and gain root privileges. (CVE-2007-3851)  It was discovered that the aacraid SCSI driver did not correctly check permissions on certain ioctls.  A local attacker could cause a denial of service or gain privileges. (CVE-2007-4308) 





[More...](http://www.ubuntu.com/usn/usn-509-1)

---

