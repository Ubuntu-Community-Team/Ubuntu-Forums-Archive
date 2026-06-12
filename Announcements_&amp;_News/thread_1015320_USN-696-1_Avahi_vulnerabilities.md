---
title: "USN-696-1: Avahi vulnerabilities"
date: 2008-12-18
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-12-18
Referenced CVEs: 
CVE-2007-3372, CVE-2008-5081


Description: 
===========================================================Ubuntu Security Notice USN-696-1          December 18, 2008avahi vulnerabilitiesCVE-2007-3372, CVE-2008-5081===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSUbuntu 7.10Ubuntu 8.04 LTSUbuntu 8.10This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  avahi-daemon                    0.6.10-0ubuntu3.5Ubuntu 7.10:  avahi-daemon                    0.6.20-2ubuntu3.4Ubuntu 8.04 LTS:  avahi-daemon                    0.6.22-2ubuntu4.1Ubuntu 8.10:  avahi-daemon                    0.6.23-2ubuntu2.1In general, a standard system upgrade is sufficient to effect thenecessary changes.Details follow:Emanuele Aina discovered that Avahi did not properly validate its input whenprocessing data over D-Bus. A local attacker could send an empty TXT messagevia D-Bus and cause a denial of service (failed assertion). This issue onlyaffected Ubuntu 6.06 LTS. (CVE-2007-3372)Hugo Dias discovered that Avahi did not properly verify its input whenprocessing mDNS packets. A remote attacker could send a crafted mDNS packetand cause a denial of service (assertion failure). (CVE-2008-5081)





[More...](http://www.ubuntu.com/usn/usn-696-1)

---

