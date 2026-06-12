---
title: "USN-568-1: PostgreSQL vulnerabilities"
date: 2008-01-14
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-01-14
Referenced CVEs:
CVE-2007-3278 CVE-2007-4769 CVE-2007-4772 CVE-2007-6067 CVE-2007-6600 CVE-2007-6601


Description:
 =========================================================== Ubuntu Security Notice USN-568-1           January 14, 2008 postgresql vulnerabilities CVE-2007-3278, CVE-2007-4769, CVE-2007-4772, CVE-2007-6067, CVE-2007-6600, CVE-2007-6601 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   postgresql-8.1                  8.1.11-0ubuntu0.6.06.1   postgresql-pltcl-8.1            8.1.11-0ubuntu0.6.06.1  Ubuntu 6.10:   postgresql-8.1                  8.1.11-0ubuntu0.6.10.1   postgresql-pltcl-8.1            8.1.11-0ubuntu0.6.10.1  Ubuntu 7.04:   postgresql-8.2                  8.2.6-0ubuntu0.7.04.1   postgresql-pltcl-8.2            8.2.6-0ubuntu0.7.04.1  Ubuntu 7.10:   postgresql-8.2                  8.2.6-0ubuntu0.7.10.1   postgresql-pltcl-8.2            8.2.6-0ubuntu0.7.10.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Nico Leidecker discovered that PostgreSQL did not properly restrict dblink functions. An authenticated user could exploit this flaw to access arbitrary accounts and execute arbitrary SQL queries. (CVE-2007-3278, CVE-2007-6601)  It was discovered that the TCL regular expression parser used by PostgreSQL did not properly check its input. An attacker could send crafted regular expressions to PostgreSQL and cause a denial of service via resource exhaustion or database crash. (CVE-2007-4769, CVE-2007-4772, CVE-2007-6067)  It was discovered that PostgreSQL executed VACUUM and ANALYZE operations within index functions with superuser privileges and also allowed SET ROLE and SET SESSION AUTHORIZATION within index functions. A remote authenticated user could exploit these flaws to gain privileges. (CVE-2007-6600) 





[More...](http://www.ubuntu.com/usn/usn-568-1)

---

