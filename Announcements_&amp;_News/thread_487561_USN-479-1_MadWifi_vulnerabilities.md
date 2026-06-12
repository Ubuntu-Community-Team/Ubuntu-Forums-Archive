---
title: "USN-479-1: MadWifi vulnerabilities"
date: 2007-06-29
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-06-29
Referenced CVEs:
CVE-2006-7177, CVE-2006-7178, CVE-2006-7179, CVE-2006-7180, CVE-2007-2829, CVE-2007-2830, CVE-2007-2831


Description:
=========================================================== Ubuntu Security Notice USN-479-1              June 28, 2007linux-restricted-modules-2.6.15/.17/.20 vulnerabilitiesCVE-2006-7177, CVE-2006-7178, CVE-2006-7179, CVE-2006-7180,CVE-2007-2829, CVE-2007-2830, CVE-2007-2831===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSUbuntu 6.10Ubuntu 7.04This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  linux-restricted-modules-2.6.15-28-386            2.6.15.12-28.2  linux-restricted-modules-2.6.15-28-686            2.6.15.12-28.2  linux-restricted-modules-2.6.15-28-amd64-generic  2.6.15.12-28.2  linux-restricted-modules-2.6.15-28-amd64-k8       2.6.15.12-28.2  linux-restricted-modules-2.6.15-28-amd64-xeon     2.6.15.12-28.2  linux-restricted-modules-2.6.15-28-k7             2.6.15.12-28.2  linux-restricted-modules-2.6.15-28-powerpc        2.6.15.12-28.2  linux-restricted-modules-2.6.15-28-powerpc-smp    2.6.15.12-28.2  linux-restricted-modules-2.6.15-28-sparc64        2.6.15.12-28.2  linux-restricted-modules-2.6.15-28-sparc64-smp    2.6.15.12-28.2Ubuntu 6.10:  linux-restricted-modules-2.6.17-11-386            2.6.17.8-11.2  linux-restricted-modules-2.6.17-11-generic        2.6.17.8-11.2  linux-restricted-modules-2.6.17-11-powerpc        2.6.17.8-11.2  linux-restricted-modules-2.6.17-11-powerpc-smp    2.6.17.8-11.2  linux-restricted-modules-2.6.17-11-powerpc64-smp  2.6.17.8-11.2  linux-restricted-modules-2.6.17-11-sparc64        2.6.17.8-11.2  linux-restricted-modules-2.6.17-11-sparc64-smp    2.6.17.8-11.2Ubuntu 7.04:  linux-restricted-modules-2.6.20-16-386            2.6.20.5-16.29  linux-restricted-modules-2.6.20-16-generic        2.6.20.5-16.29  linux-restricted-modules-2.6.20-16-lowlatency     2.6.20.5-16.29  linux-restricted-modules-2.6.20-16-powerpc        2.6.20.5-16.29  linux-restricted-modules-2.6.20-16-powerpc-smp    2.6.20.5-16.29  linux-restricted-modules-2.6.20-16-powerpc64-smp  2.6.20.5-16.29  linux-restricted-modules-2.6.20-16-sparc64        2.6.20.5-16.29  linux-restricted-modules-2.6.20-16-sparc64-smp    2.6.20.5-16.29After a standard system upgrade you need to reboot your computer toeffect the necessary changes.Details follow:Multiple flaws in the MadWifi driver were discovered that could leadto a system crash.  A physically near-by attacker could generatespecially crafted wireless network traffic and cause a denial ofservice. (CVE-2006-7177, CVE-2006-7178, CVE-2006-7179, CVE-2007-2829,CVE-2007-2830)A flaw was discovered in the MadWifi driver that would allow unencryptednetwork traffic to be sent prior to finishing WPA authentication.A physically near-by attacker could capture this, leading to a loss ofprivacy, denial of service, or network spoofing. (CVE-2006-7180)A flaw was discovered in the MadWifi driver's ioctl handling.  A localattacker could read kernel memory, or crash the system, leading to adenial of service. (CVE-2007-2831)





[More...](http://www.ubuntu.com/usn/usn-479-1)

---

