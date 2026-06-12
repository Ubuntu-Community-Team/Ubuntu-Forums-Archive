---
title: "USN-544-1: Samba vulnerabilities"
date: 2007-11-16
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-11-16
Referenced CVEs:
CVE-2007-4572 CVE-2007-5398


Description:
 ===========================================================  Ubuntu Security Notice USN-544-1          November 16, 2007 samba vulnerabilities CVE-2007-4572, CVE-2007-5398 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   samba                           3.0.22-1ubuntu3.4  Ubuntu 6.10:   samba                           3.0.22-1ubuntu4.3  Ubuntu 7.04:   samba                           3.0.24-2ubuntu1.3  Ubuntu 7.10:   samba                           3.0.26a-1ubuntu2.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Samba developers discovered that nmbd could be made to overrun a buffer during the processing of GETDC logon server requests.  When samba is configured as a Primary or Backup Domain Controller, a remote attacker could send malicious logon requests and possibly cause a denial of service. (CVE-2007-4572)  Alin Rad Pop of Secunia Research discovered that nmbd did not properly check the length of netbios packets. When samba is configured as a WINS server, a remote attacker could send multiple crafted requests resulting in the execution of arbitrary code with root privileges. (CVE-2007-5398)  





[More...](http://www.ubuntu.com/usn/usn-544-1)

---

