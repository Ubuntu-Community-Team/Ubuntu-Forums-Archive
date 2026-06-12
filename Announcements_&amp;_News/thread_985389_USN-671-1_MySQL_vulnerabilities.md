---
title: "USN-671-1: MySQL vulnerabilities"
date: 2008-11-17
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-11-17
Referenced CVEs: 
CVE-2008-2079, CVE-2008-3963, CVE-2008-4097, CVE-2008-4098


Description: 
=========================================================== Ubuntu Security Notice USN-671-1          November 17, 2008 mysql-dfsg-5.0 vulnerabilities CVE-2008-2079, CVE-2008-3963, CVE-2008-4097, CVE-2008-4098 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   mysql-server-5.0                5.0.22-0ubuntu6.06.11  Ubuntu 7.10:   mysql-server-5.0                5.0.45-1ubuntu3.4  Ubuntu 8.04 LTS:   mysql-server-5.0                5.0.51a-3ubuntu5.4  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that MySQL could be made to overwrite existing table files in the data directory. An authenticated user could use the DATA DIRECTORY and INDEX DIRECTORY options to possibly bypass privilege checks. This update alters table creation behaviour by disallowing the use of the MySQL data directory in DATA DIRECTORY and INDEX DIRECTORY options. (CVE-2008-2079, CVE-2008-4097 and CVE-2008-4098)  It was discovered that MySQL did not handle empty bit-string literals properly. An attacker could exploit this problem and cause the MySQL server to crash, leading to a denial of service. (CVE-2008-3963)





[More...](http://www.ubuntu.com/usn/USN-671-1)

---

