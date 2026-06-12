---
title: "USN-761-1: PHP vulnerabilities"
date: 2009-04-20
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-04-20
Referenced CVEs: 
                                       CVE-2008-5814, CVE-2009-0754, CVE-2009-1271        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-761-1             April 20, 2009 php5 vulnerabilities CVE-2008-5814, CVE-2009-0754, CVE-2009-1271 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libapache2-mod-php5             5.1.2-1ubuntu3.14   php5-cgi                        5.1.2-1ubuntu3.14   php5-cli                        5.1.2-1ubuntu3.14  Ubuntu 8.04 LTS:   libapache2-mod-php5             5.2.4-2ubuntu5.6   php5-cgi                        5.2.4-2ubuntu5.6   php5-cli                        5.2.4-2ubuntu5.6  Ubuntu 8.10:   libapache2-mod-php5             5.2.6-2ubuntu4.2   php5-cgi                        5.2.6-2ubuntu4.2   php5-cli                        5.2.6-2ubuntu4.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that PHP did not sanitize certain error messages when display_errors is enabled, which could result in browsers becoming vulnerable to cross-site scripting attacks when processing the output. With cross-site scripting vulnerabilities, if a user were tricked into viewing server output during a crafted server request, a remote attacker could exploit this to modify the contents, or steal confidential data (such as passwords), within the same domain. (CVE-2008-5814)  It was discovered that PHP did not properly handle the mbstring.func_overload setting within .htaccess files when using virtual hosts. A virtual host administrator could use this flaw to cause settings to be applied to other virtual hosts on the same server. (CVE-2009-0754)  It was discovered that PHP did not properly handle certain malformed strings when being parsed by the json_decode function. A remote attacker could exploit this flaw and cause the PHP server to crash, resulting in a denial of service. This issue only affected Ubuntu 8.04 and 8.10. (CVE-2009-1271)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-761-1)

---

