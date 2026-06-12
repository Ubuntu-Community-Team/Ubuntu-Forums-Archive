---
title: "USN-549-2: PHP regression"
date: 2007-12-04
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-12-04
Description:
 ===========================================================  Ubuntu Security Notice USN-549-2          December 03, 2007 php5 regression [https://launchpad.net/bugs/173043](https://launchpad.net/bugs/173043) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 7.10:   libapache2-mod-php5             5.2.3-1ubuntu6.2   php5-cgi                        5.2.3-1ubuntu6.2   php5-cli                        5.2.3-1ubuntu6.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  USN-549-1 fixed vulnerabilities in PHP.  However, some upstream changes were incomplete, which caused crashes in certain situations with Ubuntu 7.10.  This update fixes the problem.  We apologize for the inconvenience.  Original advisory details:   It was discovered that the wordwrap function did not correctly  check lengths.  Remote attackers could exploit this to cause  a crash or monopolize CPU resources, resulting in a denial of  service. (CVE-2007-3998)   Integer overflows were discovered in the strspn and strcspn functions.  Attackers could exploit this to read arbitrary areas of memory, possibly  gaining access to sensitive information. (CVE-2007-4657)   Stanislav Malyshev discovered that money_format function did not correctly  handle certain tokens.  If a PHP application were tricked into processing  a bad format string, a remote attacker could execute arbitrary code with  application privileges. (CVE-2007-4658)   It was discovered that the php_openssl_make_REQ function did not  correctly check buffer lengths.  A remote attacker could send a  specially crafted message and execute arbitrary code with application  privileges. (CVE-2007-4662)   It was discovered that certain characters in session cookies were not  handled correctly.  A remote attacker could injection values which could  lead to altered application behavior, potentially gaining additional  privileges. (CVE-2007-3799)   Gerhard Wagner discovered that the chunk_split function did not  correctly handle long strings.  A remote attacker could exploit this  to execute arbitrary code with application privileges.  (CVE-2007-2872,  CVE-2007-4660, CVE-2007-4661)   Stefan Esser discovered that deeply nested arrays could be made to  fill stack space.  A remote attacker could exploit this to cause a  crash or monopolize CPU resources, resulting in a denial of service.  (CVE-2007-1285, CVE-2007-4670)   Rasmus Lerdorf discovered that the htmlentities and htmlspecialchars  functions did not correctly stop when handling partial multibyte  sequences.  A remote attacker could exploit this to read certain areas of  memory, possibly gaining access to sensitive information. (CVE-2007-5898)   It was discovered that the output_add_rewrite_var fucntion would  sometimes leak session id information to forms targeting remote URLs.  Malicious remote sites could use this information to gain access to a  PHP application user's login credentials. (CVE-2007-5899) 





[More...](http://www.ubuntu.com/usn/usn-549-2)

---

