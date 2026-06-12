---
title: "USN-707-1: CUPS vulnerabilities"
date: 2009-01-12
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-01-12
Referenced CVEs: 
CVE-2008-5183, CVE-2008-5184, CVE-2008-5286, CVE-2008-5377


Description: 
=========================================================== Ubuntu Security Notice USN-707-1           January 12, 2009 cups, cupsys vulnerabilities CVE-2008-5183, CVE-2008-5184, CVE-2008-5286, CVE-2008-5377 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   cupsys                          1.2.2-0ubuntu0.6.06.12  Ubuntu 7.10:   cupsys                          1.3.2-1ubuntu7.9  Ubuntu 8.04 LTS:   cupsys                          1.3.7-1ubuntu3.3  Ubuntu 8.10:   cups                            1.3.9-2ubuntu6.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that CUPS didn't properly handle adding a large number of RSS subscriptions. A local user could exploit this and cause CUPS to crash, leading to a denial of service. This issue only applied to Ubuntu 7.10, 8.04 LTS and 8.10. (CVE-2008-5183)  It was discovered that CUPS did not authenticate users when adding and cancelling RSS subscriptions. An unprivileged local user could bypass intended restrictions and add a large number of RSS subscriptions. This issue only applied to Ubuntu 7.10 and 8.04 LTS. (CVE-2008-5184)  It was discovered that the PNG filter in CUPS did not properly handle certain malformed images. If a user or automated system were tricked into opening a crafted PNG image file, a remote attacker could cause a denial of service or execute arbitrary code with user privileges. In Ubuntu 7.10, 8.04 LTS, and 8.10, attackers would be isolated by the AppArmor CUPS profile. (CVE-2008-5286)  It was discovered that the example pstopdf CUPS filter created log files in an insecure way. Local users could exploit a race condition to create or overwrite files with the privileges of the user invoking the program. This issue only applied to Ubuntu 6.06 LTS, 7.10, and 8.04 LTS. (CVE-2008-5377)





[More...](http://www.ubuntu.com/usn/USN-707-1)

---

