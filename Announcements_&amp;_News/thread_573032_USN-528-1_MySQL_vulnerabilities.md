---
title: "USN-528-1: MySQL vulnerabilities"
date: 2007-10-11
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-10-11
Referenced CVEs:
CVE-2007-2583, CVE-2007-2691, CVE-2007-3780, CVE-2007-3782


Description:
 ===========================================================  Ubuntu Security Notice USN-528-1           October 11, 2007 mysql-dfsg-5.0 vulnerabilities CVE-2007-2583, CVE-2007-2691, CVE-2007-3780, CVE-2007-3782 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   mysql-server-5.0                5.0.22-0ubuntu6.06.5  Ubuntu 6.10:   mysql-server-5.0                5.0.24a-9ubuntu2.1  Ubuntu 7.04:   mysql-server-5.0                5.0.38-0ubuntu1.1  In general, a standard system upgrade is sufficient to affect the necessary changes.  ATTENTION: A change was made to the init script for mysql.  Now on start-up, mysql is checked to make sure that the mysql root password is set. If it is blank, a message is sent to the console and the system logger alerting that the password is not set, along with instructions on how to set it. Additionally, you can now use:    sudo /etc/init.d/mysql reset-password  to set the root mysql user's password.  Details follow:  Neil Kettle discovered that MySQL could be made to dereference a NULL pointer and divide by zero.  An authenticated user could exploit this with a crafted IF clause, leading to a denial of service. (CVE-2007-2583)  Victoria Reznichenko discovered that MySQL did not always require the DROP privilege.  An authenticated user could exploit this via RENAME TABLE statements to rename arbitrary tables, possibly gaining additional database access. (CVE-2007-2691)  It was discovered that MySQL could be made to overflow a signed char during authentication.  Remote attackers could use crafted authentication requests to cause a denial of service. (CVE-2007-3780)  Phil Anderton discovered that MySQL did not properly verify access privileges when accessing external tables.  As a result, authenticated users could exploit this to obtain UPDATE privileges to external tables. (CVE-2007-3782)  In certain situations, when installing or upgrading mysql, there was no notification that the mysql root user password needed to be set.  If the password was left unset, attackers would be able to obtain unrestricted access to mysql.  This is now checked during mysql start-up. 





[More...](http://www.ubuntu.com/usn/usn-528-1)

---

