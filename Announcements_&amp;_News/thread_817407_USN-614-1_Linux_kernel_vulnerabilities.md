---
title: "USN-614-1: Linux kernel vulnerabilities"
date: 2008-06-03
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-06-03
Referenced CVEs: 
CVE-2007-6694, CVE-2008-1375, CVE-2008-1669, CVE-2008-1675


Description: 
 ===========================================================  Ubuntu Security Notice USN-614-1              June 03, 2008 linux vulnerabilities CVE-2007-6694, CVE-2008-1375, CVE-2008-1669, CVE-2008-1675 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   linux-image-2.6.24-18-386       2.6.24-18.32   linux-image-2.6.24-18-generic   2.6.24-18.32   linux-image-2.6.24-18-hppa32    2.6.24-18.32   linux-image-2.6.24-18-hppa64    2.6.24-18.32   linux-image-2.6.24-18-itanium   2.6.24-18.32   linux-image-2.6.24-18-lpia      2.6.24-18.32   linux-image-2.6.24-18-lpiacompat  2.6.24-18.32   linux-image-2.6.24-18-mckinley  2.6.24-18.32   linux-image-2.6.24-18-openvz    2.6.24-18.32   linux-image-2.6.24-18-powerpc   2.6.24-18.32   linux-image-2.6.24-18-powerpc-smp  2.6.24-18.32   linux-image-2.6.24-18-powerpc64-smp  2.6.24-18.32   linux-image-2.6.24-18-rt        2.6.24-18.32   linux-image-2.6.24-18-server    2.6.24-18.32   linux-image-2.6.24-18-sparc64   2.6.24-18.32   linux-image-2.6.24-18-sparc64-smp  2.6.24-18.32   linux-image-2.6.24-18-virtual   2.6.24-18.32   linux-image-2.6.24-18-xen       2.6.24-18.32  After a standard system upgrade you need to reboot your computer to effect the necessary changes.  ATTENTION: Due to an unavoidable ABI change the kernel updates have been given a new version number, which requires you to recompile and reinstall all third party kernel modules you might have installed. If you use linux-restricted-modules, you have to update that package as well to get modules which work with the new kernel version. Unless you manually uninstalled the standard kernel metapackages (e.g. linux-386, linux-powerpc, linux-amd64-generic), a standard system upgrade will automatically perform this as well.  Details follow:  It was discovered that PowerPC kernels did not correctly handle reporting certain system details.  By requesting a specific set of information, a local attacker could cause a system crash resulting in a denial of service. (CVE-2007-6694)  A race condition was discovered between dnotify fcntl() and close() in the kernel.  If a local attacker performed malicious dnotify requests, they could cause memory consumption leading to a denial of service, or possibly send arbitrary signals to any process. (CVE-2008-1375)  On SMP systems, a race condition existed in fcntl().  Local attackers could perform malicious locks, causing system crashes and leading to a denial of service. (CVE-2008-1669)  The tehuti network driver did not correctly handle certain IO functions. A local attacker could perform malicious requests to the driver, potentially accessing kernel memory, leading to privilege escalation or access to private system information. (CVE-2008-1675) 





[More...](http://www.ubuntu.com/usn/usn-614-1)

---

