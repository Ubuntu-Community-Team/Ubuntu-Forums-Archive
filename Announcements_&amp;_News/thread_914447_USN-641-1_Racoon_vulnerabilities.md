---
title: "USN-641-1: Racoon vulnerabilities"
date: 2008-09-08
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-09-08
Referenced CVEs: 
CVE-2008-3651, CVE-2008-3652


Description: 
 ===========================================================  Ubuntu Security Notice USN-641-1         September 09, 2008 ipsec-tools vulnerabilities CVE-2008-3651, CVE-2008-3652 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   racoon                          1:0.6.5-4ubuntu1.2  Ubuntu 7.04:   racoon                          1:0.6.6-3ubuntu3.1  Ubuntu 7.10:   racoon                          1:0.6.6-3.1ubuntu3.1  Ubuntu 8.04 LTS:   racoon                          1:0.6.7-1.1ubuntu1.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that there were multiple ways to leak memory during the IKE negotiation when handling certain packets.  If a remote attacker sent repeated malicious requests, the "racoon" key exchange server could allocate large amounts of memory, possibly leading to a denial of service. 





[More...](http://www.ubuntu.com/usn/usn-641-1)

---

