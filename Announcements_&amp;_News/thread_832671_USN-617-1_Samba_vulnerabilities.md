---
title: "USN-617-1: Samba vulnerabilities"
date: 2008-06-17
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-06-17
Referenced CVEs: 
CVE-2007-4572, CVE-2008-1105


Description: 
 ===========================================================  Ubuntu Security Notice USN-617-1              June 17, 2008 samba vulnerabilities CVE-2007-4572, CVE-2008-1105 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libsmbclient                    3.0.22-1ubuntu3.7   samba                           3.0.22-1ubuntu3.7  Ubuntu 7.04:   libsmbclient                    3.0.24-2ubuntu1.6   samba                           3.0.24-2ubuntu1.6  Ubuntu 7.10:   libsmbclient                    3.0.26a-1ubuntu2.4   samba                           3.0.26a-1ubuntu2.4  Ubuntu 8.04 LTS:   libsmbclient                    3.0.28a-1ubuntu4.2   samba                           3.0.28a-1ubuntu4.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Samba developers discovered that nmbd could be made to overrun a buffer during the processing of GETDC logon server requests. When samba is configured as a Primary or Backup Domain Controller, a remote attacker could send malicious logon requests and possibly cause a denial of service. (CVE-2007-4572)  Alin Rad Pop of Secunia Research discovered that Samba did not properly perform bounds checking when parsing SMB replies. A remote attacker could send crafted SMB packets and execute arbitrary code. (CVE-2008-1105) 





[More...](http://www.ubuntu.com/usn/usn-617-1)

---

