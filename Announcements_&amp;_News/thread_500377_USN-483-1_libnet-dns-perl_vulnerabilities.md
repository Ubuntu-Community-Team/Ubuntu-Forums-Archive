---
title: "USN-483-1: libnet-dns-perl vulnerabilities"
date: 2007-07-13
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-07-13
Referenced CVEs:
CVE-2007-3377, CVE-2007-3409


Description:
 ===========================================================  Ubuntu Security Notice USN-483-1              July 11, 2007 libnet-dns-perl vulnerabilities CVE-2007-3377, CVE-2007-3409 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libnet-dns-perl                          0.53-2ubuntu1  Ubuntu 6.10:   libnet-dns-perl                          0.57-1ubuntu1  After a standard system upgrade you need to reboot your computer to effect the necessary changes.  Details follow:  Peter Johannes Holzer discovered that the Net::DNS Perl module had predictable sequence numbers.  This could allow remote attackers to carry out DNS spoofing, leading to possible man-in-the-middle attacks. (CVE-2007-3377)  Steffen Ullrich discovered that the Net::DNS Perl module did not correctly detect recursive compressed responses.  A remote attacker could send a specially crafted packet, causing applications using Net::DNS to crash or monopolize CPU resources, leading to a denial of service.  (CVE-2007-3409) 





[More...](http://www.ubuntu.com/usn/usn-483-1)

---

