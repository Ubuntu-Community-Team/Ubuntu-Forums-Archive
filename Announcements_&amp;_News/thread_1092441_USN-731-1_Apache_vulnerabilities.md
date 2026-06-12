---
title: "USN-731-1: Apache vulnerabilities"
date: 2009-03-10
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-03-10
Referenced CVEs: 
CVE-2007-6203, CVE-2007-6420, CVE-2008-1678, CVE-2008-2168, CVE-2008-2364, CVE-2008-2939


Description: 
=========================================================== Ubuntu Security Notice USN-731-1             March 10, 2009 apache2 vulnerabilities CVE-2007-6203, CVE-2007-6420, CVE-2008-1678, CVE-2008-2168, CVE-2008-2364, CVE-2008-2939 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   apache2-common                  2.0.55-4ubuntu2.4   apache2-mpm-perchild            2.0.55-4ubuntu2.4   apache2-mpm-prefork             2.0.55-4ubuntu2.4   apache2-mpm-worker              2.0.55-4ubuntu2.4  Ubuntu 7.10:   apache2-mpm-event               2.2.4-3ubuntu0.2   apache2-mpm-perchild            2.2.4-3ubuntu0.2   apache2-mpm-prefork             2.2.4-3ubuntu0.2   apache2-mpm-worker              2.2.4-3ubuntu0.2   apache2.2-common                2.2.4-3ubuntu0.2  Ubuntu 8.04 LTS:   apache2-mpm-event               2.2.8-1ubuntu0.4   apache2-mpm-perchild            2.2.8-1ubuntu0.4   apache2-mpm-prefork             2.2.8-1ubuntu0.4   apache2-mpm-worker              2.2.8-1ubuntu0.4   apache2.2-common                2.2.8-1ubuntu0.4  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that Apache did not sanitize the method specifier header from an HTTP request when it is returned in an error message, which could result in browsers becoming vulnerable to cross-site scripting attacks when processing the output. With cross-site scripting vulnerabilities, if a user were tricked into viewing server output during a crafted server request, a remote attacker could exploit this to modify the contents, or steal confidential data (such as passwords), within the same domain. This issue only affected Ubuntu 6.06 LTS and 7.10. (CVE-2007-6203)  It was discovered that Apache was vulnerable to a cross-site request forgery (CSRF) in the mod_proxy_balancer balancer manager. If an Apache administrator were tricked into clicking a link on a specially crafted web page, an attacker could trigger commands that could modify the balancer manager configuration. This issue only affected Ubuntu 7.10 and 8.04 LTS. (CVE-2007-6420)  It was discovered that Apache had a memory leak when using mod_ssl with compression. A remote attacker could exploit this to exhaust server memory, leading to a denial of service. This issue only affected Ubuntu 7.10. (CVE-2008-1678)  It was discovered that in certain conditions, Apache did not specify a default character set when returning certain error messages containing UTF-7 encoded data, which could result in browsers becoming vulnerable to cross-site scripting attacks when processing the output. This issue only affected Ubuntu 6.06 LTS and 7.10. (CVE-2008-2168)  It was discovered that when configured as a proxy server, Apache did not limit the number of forwarded interim responses. A malicious remote server could send a large number of interim responses and cause a denial of service via memory exhaustion. (CVE-2008-2364)  It was discovered that mod_proxy_ftp did not sanitize wildcard pathnames when they are returned in directory listings, which could result in browsers becoming vulnerable to cross-site scripting attacks when processing the output. (CVE-2008-2939)





[More...](http://www.ubuntu.com/usn/USN-731-1)

---

