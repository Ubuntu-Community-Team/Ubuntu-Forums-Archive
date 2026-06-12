---
title: "USN-508-1: Linux kernel vulnerabilities"
date: 2007-08-31
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-08-31
Referenced CVEs:
CVE-2005-0504, CVE-2007-2242, CVE-2007-3104, CVE-2007-3105, CVE-2007-3848, CVE-2007-4308


Description:
 ===========================================================  Ubuntu Security Notice USN-508-1            August 31, 2007 linux-source-2.6.15 vulnerabilities CVE-2005-0504, CVE-2007-2242, CVE-2007-3104, CVE-2007-3105, CVE-2007-3848, CVE-2007-4308 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   linux-image-2.6.15-29-386                    2.6.15-29.58   linux-image-2.6.15-29-686                    2.6.15-29.58   linux-image-2.6.15-29-amd64-generic          2.6.15-29.58   linux-image-2.6.15-29-amd64-k8               2.6.15-29.58   linux-image-2.6.15-29-amd64-server           2.6.15-29.58   linux-image-2.6.15-29-amd64-xeon             2.6.15-29.58   linux-image-2.6.15-29-hppa32                 2.6.15-29.58   linux-image-2.6.15-29-hppa32-smp             2.6.15-29.58   linux-image-2.6.15-29-hppa64                 2.6.15-29.58   linux-image-2.6.15-29-hppa64-smp             2.6.15-29.58   linux-image-2.6.15-29-itanium                2.6.15-29.58   linux-image-2.6.15-29-itanium-smp            2.6.15-29.58   linux-image-2.6.15-29-k7                     2.6.15-29.58   linux-image-2.6.15-29-mckinley               2.6.15-29.58   linux-image-2.6.15-29-mckinley-smp           2.6.15-29.58   linux-image-2.6.15-29-powerpc                2.6.15-29.58   linux-image-2.6.15-29-powerpc-smp            2.6.15-29.58   linux-image-2.6.15-29-powerpc64-smp          2.6.15-29.58   linux-image-2.6.15-29-server                 2.6.15-29.58   linux-image-2.6.15-29-server-bigiron         2.6.15-29.58   linux-image-2.6.15-29-sparc64                2.6.15-29.58   linux-image-2.6.15-29-sparc64-smp            2.6.15-29.58  After a standard system upgrade you need to reboot your computer to effect the necessary changes.  ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. If you use linux-restricted-modules, you have to update that package as well to get modules which work with the new kernel version. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-386, linux-powerpc, linux-amd64-generic), a standard system upgrade will automatically perform this as well.  Details follow:  A buffer overflow was discovered in the Moxa serial driver.  Local attackers could execute arbitrary code and gain root privileges. (CVE-2005-0504)  A flaw was discovered in the IPv6 stack's handling of type 0 route headers. By sending a specially crafted IPv6 packet, a remote attacker could cause a denial of service between two IPv6 hosts. (CVE-2007-2242)  A flaw in the sysfs_readdir function allowed a local user to cause a denial of service by dereferencing a NULL pointer. (CVE-2007-3104)  A buffer overflow was discovered in the random number generator.  In environments with granular assignment of root privileges, a local attacker could gain additional privileges. (CVE-2007-3105)  It was discovered that certain setuid-root processes did not correctly reset process death signal handlers.  A local user could manipulate this to send signals to processes they would not normally have access to. (CVE-2007-3848)  It was discovered that the aacraid SCSI driver did not correctly check permissions on certain ioctls.  A local attacker could cause a denial of service or gain privileges. (CVE-2007-4308) 





[More...](http://www.ubuntu.com/usn/usn-508-1)

---

