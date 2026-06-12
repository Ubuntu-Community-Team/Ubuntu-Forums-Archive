---
title: "USN-761-2: PHP vulnerabilities"
date: 2009-04-27
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-04-27
Referenced CVEs: 
                                       CVE-2008-5814, CVE-2009-1271        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-761-2             April 27, 2009 php5 vulnerabilities CVE-2008-5814, CVE-2009-1271 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 9.04:   libapache2-mod-php5             5.2.6.dfsg.1-3ubuntu4.1   php5-cgi                        5.2.6.dfsg.1-3ubuntu4.1   php5-cli                        5.2.6.dfsg.1-3ubuntu4.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  USN-761-1 fixed vulnerabilities in PHP. This update provides the corresponding updates for Ubuntu 9.04.  Original advisory details:   It was discovered that PHP did not sanitize certain error messages when  display_errors is enabled, which could result in browsers becoming  vulnerable to cross-site scripting attacks when processing the output.  With cross-site scripting vulnerabilities, if a user were tricked into  viewing server output during a crafted server request, a remote attacker  could exploit this to modify the contents, or steal confidential data  (such as passwords), within the same domain. (CVE-2008-5814)    It was discovered that PHP did not properly handle certain malformed  strings when being parsed by the json_decode function. A remote attacker  could exploit this flaw and cause the PHP server to crash, resulting in a  denial of service. This issue only affected Ubuntu 8.04 and 8.10.  (CVE-2009-1271)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-761-2)

---

