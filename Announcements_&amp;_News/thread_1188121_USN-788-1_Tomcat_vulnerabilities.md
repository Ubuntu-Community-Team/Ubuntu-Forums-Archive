---
title: "USN-788-1: Tomcat vulnerabilities"
date: 2009-06-15
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-06-15
Referenced CVEs: 
                                       CVE-2008-5515, CVE-2009-0033, CVE-2009-0580, CVE-2009-0781, CVE-2009-0783        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-788-1              June 15, 2009 tomcat6 vulnerabilities CVE-2008-5515, CVE-2009-0033, CVE-2009-0580, CVE-2009-0781, CVE-2009-0783 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.10:   libtomcat6-java                 6.0.18-0ubuntu3.2   tomcat6-examples                6.0.18-0ubuntu3.2  Ubuntu 9.04:   libtomcat6-java                 6.0.18-0ubuntu6.1   tomcat6-examples                6.0.18-0ubuntu6.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Iida Minehiko discovered that Tomcat did not properly normalise paths. A remote attacker could send specially crafted requests to the server and bypass security restrictions, gaining access to sensitive content. (CVE-2008-5515)  Yoshihito Fukuyama discovered that Tomcat did not properly handle errors when the Java AJP connector and mod_jk load balancing are used. A remote attacker could send specially crafted requests containing invalid headers to the server and cause a temporary denial of service. (CVE-2009-0033)  D. Matscheko and T. Hackner discovered that Tomcat did not properly handle malformed URL encoding of passwords when FORM authentication is used. A remote attacker could exploit this in order to enumerate valid usernames. (CVE-2009-0580)  Deniz Cevik discovered that Tomcat did not properly escape certain parameters in the example calendar application which could result in browsers becoming vulnerable to cross-site scripting attacks when processing the output. With cross-site scripting vulnerabilities, if a user were tricked into viewing server output during a crafted server request, a remote attacker could exploit this to modify the contents, or steal confidential data (such as passwords), within the same domain. (CVE-2009-0781)  Philippe Prados discovered that Tomcat allowed web applications to replace the XML parser used by other web applications. Local users could exploit this to bypass security restrictions and gain access to certain sensitive files. (CVE-2009-0783)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-788-1)

---

