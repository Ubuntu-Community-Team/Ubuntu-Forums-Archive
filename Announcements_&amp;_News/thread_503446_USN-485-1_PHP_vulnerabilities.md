---
title: "USN-485-1: PHP vulnerabilities"
date: 2007-07-17
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-07-17
Referenced CVEs:
CVE-2007-1864, CVE-2007-2728


Description:
 ===========================================================  Ubuntu Security Notice USN-485-1              July 17, 2007 php5 vulnerabilities CVE-2007-1864, CVE-2007-2728 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libapache2-mod-php5                      5.1.2-1ubuntu3.9   php5-xmlrpc                              5.1.2-1ubuntu3.9  Ubuntu 6.10:   libapache2-mod-php5                      5.1.6-1ubuntu2.6   php5-xmlrpc                              5.1.6-1ubuntu2.6  Ubuntu 7.04:   libapache2-mod-php5                      5.2.1-0ubuntu1.4   php5-xmlrpc                              5.2.1-0ubuntu1.4  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that the PHP xmlrpc extension did not correctly check heap memory allocation sizes.  A remote attacker could send a specially crafted request to a PHP application using xmlrpc and execute arbitrary code as the Apache user. (CVE-2007-1864)  Stefan Esser discovered a flaw in the random number initialization of the PHP SOAP extension.  This could lead to remote attackers being able to predict certain elements of the authentication mechanism. (CVE-2007-2728) 





[More...](http://www.ubuntu.com/usn/usn-485-1)

---

