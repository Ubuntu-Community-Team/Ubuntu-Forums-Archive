---
title: "USN-551-1: OpenLDAP vulnerabilities"
date: 2007-12-04
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-12-04
Referenced CVEs:
CVE-2007-5707 CVE-2007-5708


Description:
 =========================================================== Ubuntu Security Notice USN-551-1          December 04, 2007 openldap vulnerabilities CVE-2007-5707, CVE-2007-5708 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   slapd                           2.2.26-5ubuntu2.4  Ubuntu 6.10:   slapd                           2.2.26-5ubuntu3.2  Ubuntu 7.04:   slapd                           2.3.30-2ubuntu0.1  Ubuntu 7.10:   slapd                           2.3.35-1ubuntu0.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Thomas Sesselmann discovered that the OpenLDAP slapd server did not properly handle certain modify requests. A remote attacker could send malicious modify requests to the server and cause a denial of service. (CVE-2007-5707)  Toby Blake discovered that slapd did not properly terminate an array while running as a proxy-caching server. A remote attacker may be able to send crafted search requests to the server and cause a denial of service. This issue only affects Ubuntu 7.04 and 7.10. (CVE-2007-5708)  





[More...](http://www.ubuntu.com/usn/usn-551-1)

---

