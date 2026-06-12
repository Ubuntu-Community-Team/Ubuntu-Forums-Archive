---
title: "USN-520-1: fetchmail vulnerabilities"
date: 2007-09-26
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-09-26
Referenced CVEs:
CVE-2007-1558, CVE-2007-4565


Description:
 ===========================================================  Ubuntu Security Notice USN-520-1         September 26, 2007 fetchmail vulnerabilities CVE-2007-1558, CVE-2007-4565 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   fetchmail                       6.3.2-2ubuntu2.2  Ubuntu 6.10:   fetchmail                       6.3.4-1ubuntu4.2  Ubuntu 7.04:   fetchmail                       6.3.6-1ubuntu2.1  In general, a standard system upgrade is sufficient to affect the necessary changes.  Details follow:  Gaetan Leurent discovered a vulnerability in the APOP protocol based on MD5 collisions. As fetchmail supports the APOP protocol, this vulnerability can be used by attackers to discover a portion of the APOP user's authentication credentials. (CVE-2007-1558)  Earl Chew discovered that fetchmail can be made to de-reference a NULL pointer when contacting SMTP servers. This vulnerability can be used by attackers who control the SMTP server to crash fetchmail and cause a denial of service. (CVE-2007-4565) 





[More...](http://www.ubuntu.com/usn/usn-520-1)

---

