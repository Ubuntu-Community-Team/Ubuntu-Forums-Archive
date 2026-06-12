---
title: "USN-575-1: Apache vulnerabilities"
date: 2008-02-04
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-02-04
Referenced CVEs:
CVE-2006-3918, CVE-2007-3847, CVE-2007-4465, CVE-2007-5000, CVE-2007-6388, CVE-2007-6421, CVE-2007-6422, CVE-2008-0005


Description:
 ===========================================================  Ubuntu Security Notice USN-575-1          February 04, 2008 apache2 vulnerabilities CVE-2006-3918, CVE-2007-3847, CVE-2007-4465, CVE-2007-5000, CVE-2007-6388, CVE-2007-6421, CVE-2007-6422, CVE-2008-0005 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   apache2-mpm-perchild            2.0.55-4ubuntu2.3   apache2-mpm-prefork             2.0.55-4ubuntu2.3   apache2-mpm-worker              2.0.55-4ubuntu2.3  Ubuntu 6.10:   apache2-mpm-perchild            2.0.55-4ubuntu4.2   apache2-mpm-prefork             2.0.55-4ubuntu4.2   apache2-mpm-worker              2.0.55-4ubuntu4.2  Ubuntu 7.04:   apache2-mpm-event               2.2.3-3.2ubuntu2.1   apache2-mpm-perchild            2.2.3-3.2ubuntu2.1   apache2-mpm-prefork             2.2.3-3.2ubuntu2.1   apache2-mpm-worker              2.2.3-3.2ubuntu2.1  Ubuntu 7.10:   apache2-mpm-event               2.2.4-3ubuntu0.1   apache2-mpm-perchild            2.2.4-3ubuntu0.1   apache2-mpm-prefork             2.2.4-3ubuntu0.1   apache2-mpm-worker              2.2.4-3ubuntu0.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that Apache did not sanitize the Expect header from an HTTP request when it is reflected back in an error message, which could result in browsers becoming vulnerable to cross-site scripting attacks when processing the output. With cross-site scripting vulnerabilities, if a user were tricked into viewing server output during a crafted server request, a remote attacker could exploit this to modify the contents, or steal confidential data (such as passwords), within the same domain. This was only vulnerable in Ubuntu 6.06. (CVE-2006-3918)  It was discovered that when configured as a proxy server and using a threaded MPM, Apache did not properly sanitize its input. A remote attacker could send Apache crafted date headers and cause a denial of service via application crash. By default, mod_proxy is disabled in Ubuntu. (CVE-2007-3847)  It was discovered that mod_autoindex did not force a character set, which could result in browsers becoming vulnerable to cross-site scripting attacks when processing the output. (CVE-2007-4465)  It was discovered that mod_imap/mod_imagemap did not force a character set, which could result in browsers becoming vulnerable to cross-site scripting attacks when processing the output. By default, mod_imap/mod_imagemap is disabled in Ubuntu. (CVE-2007-5000)  It was discovered that mod_status when status pages were available, allowed for cross-site scripting attacks. By default, mod_status is disabled in Ubuntu. (CVE-2007-6388)  It was discovered that mod_proxy_balancer did not sanitize its input, which could result in browsers becoming vulnerable to cross-site scripting attacks when processing the output. By default, mod_proxy_balancer is disabled in Ubuntu. This was only vulnerable in Ubuntu 7.04 and 7.10. (CVE-2007-6421)  It was discovered that mod_proxy_balancer could be made to dereference a NULL pointer. A remote attacker could send a crafted request and cause a denial of service via application crash. By default, mod_proxy_balancer is disabled in Ubuntu. This was only vulnerable in Ubuntu 7.04 and 7.10. (CVE-2007-6422)  It was discovered that mod_proxy_ftp did not force a character set, which could result in browsers becoming vulnerable to cross-site scripting attacks when processing the output. By default, mod_proxy_ftp is disabled in Ubuntu. (CVE-2008-0005) 





[More...](http://www.ubuntu.com/usn/usn-575-1)

---

