---
title: "USN-563-1: CUPS vulnerabilities"
date: 2008-01-09
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-01-09
Referenced CVEs:
CVE-2007-5849, CVE-2007-6358


Description:
 ===========================================================  Ubuntu Security Notice USN-563-1           January 09, 2008 cupsys vulnerabilities CVE-2007-5849, CVE-2007-6358 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   cupsys                          1.2.2-0ubuntu0.6.06.6  Ubuntu 6.10:   cupsys                          1.2.4-2ubuntu3.2  Ubuntu 7.04:   cupsys                          1.2.8-0ubuntu8.2  Ubuntu 7.10:   cupsys                          1.3.2-1ubuntu7.3  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Wei Wang discovered that the SNMP discovery backend did not correctly calculate the length of strings.  If a user were tricked into scanning for printers, a remote attacker could send a specially crafted packet and possibly execute arbitrary code.  Elias Pipping discovered that temporary files were not handled safely in certain situations when converting PDF to PS.  A local attacker could cause a denial of service. 





[More...](http://www.ubuntu.com/usn/usn-563-1)

---

