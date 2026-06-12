---
title: "USN-559-1: MySQL vulnerabilities"
date: 2007-12-21
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-12-21
Referenced CVEs:
CVE-2007-3781 CVE-2007-5925 CVE-2007-5969 CVE-2007-6304


Description:
 =========================================================== Ubuntu Security Notice USN-559-1          December 21, 2007 mysql-dfsg-5.0 vulnerabilities CVE-2007-3781, CVE-2007-5925, CVE-2007-5969, CVE-2007-6304 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   mysql-server-5.0                5.0.22-0ubuntu6.06.6  Ubuntu 6.10:   mysql-server-5.0                5.0.24a-9ubuntu2.2  Ubuntu 7.04:   mysql-server-5.0                5.0.38-0ubuntu1.2  Ubuntu 7.10:   mysql-server-5.0                5.0.45-1ubuntu3.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Joe Gallo and Artem Russakovskii discovered that the InnoDB engine in MySQL did not properly perform input validation. An authenticated user could use a crafted CONTAINS statement to cause a denial of service. (CVE-2007-5925)  It was discovered that under certain conditions MySQL could be made to overwrite system table information. An authenticated user could use a crafted RENAME statement to escalate privileges. (CVE-2007-5969)  Philip Stoev discovered that the the federated engine of MySQL did not properly handle responses with a small number of columns. An authenticated user could use a crafted response to a SHOW TABLE STATUS query and cause a denial of service. (CVE-2007-6304)  It was discovered that MySQL did not properly enforce access controls. An authenticated user could use a crafted CREATE TABLE LIKE statement to escalate privileges. (CVE-2007-3781)  





[More...](http://www.ubuntu.com/usn/usn-559-1)

---

