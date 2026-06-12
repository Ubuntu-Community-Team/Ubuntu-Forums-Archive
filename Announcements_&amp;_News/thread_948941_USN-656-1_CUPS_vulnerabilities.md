---
title: "USN-656-1: CUPS vulnerabilities"
date: 2008-10-15
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-10-15
Referenced CVEs: 
CVE-2008-1722, CVE-2008-3639, CVE-2008-3640, CVE-2008-3641


Description: 
 =========================================================== Ubuntu Security Notice USN-656-1           October 15, 2008 cupsys vulnerabilities CVE-2008-1722, CVE-2008-3639, CVE-2008-3640, CVE-2008-3641 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   cupsys                          1.2.2-0ubuntu0.6.06.11  Ubuntu 7.04:   cupsys                          1.2.8-0ubuntu8.6  Ubuntu 7.10:   cupsys                          1.3.2-1ubuntu7.8  Ubuntu 8.04 LTS:   cupsys                          1.3.7-1ubuntu3.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that the SGI image filter in CUPS did not perform proper bounds checking. If a user or automated system were tricked into opening a crafted SGI image, an attacker could cause a denial of service. (CVE-2008-3639)  It was discovered that the texttops filter in CUPS did not properly validate page metrics. If a user or automated system were tricked into opening a crafted text file, an attacker could cause a denial of service. (CVE-2008-3640)  It was discovered that the HP-GL filter in CUPS did not properly check for invalid pen parameters. If a user or automated system were tricked into opening a crafted HP-GL or HP-GL/2 file, a remote attacker could cause a denial of service or execute arbitrary code with user privileges. In Ubuntu 7.10 and 8.04 LTS, attackers would be isolated by the AppArmor CUPS profile. (CVE-2008-3641)  NOTE: The previous update for CUPS on Ubuntu 6.06 LTS did not have the the fix for CVE-2008-1722 applied. This update includes fixes for the problem. We apologize for the inconvenience. 





[More...](http://www.ubuntu.com/usn/usn-656-1)

---

