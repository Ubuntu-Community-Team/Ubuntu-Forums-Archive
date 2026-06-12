---
title: "USN-826-1: Mono vulnerabilities"
date: 2009-08-26
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-08-26
Referenced CVEs: 
                                       CVE-2008-3422, CVE-2008-3906, CVE-2009-0217        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-826-1            August 26, 2009 mono vulnerabilities CVE-2008-3422, CVE-2008-3906, CVE-2009-0217 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   libmono-security1.0-cil         1.2.6+dfsg-6ubuntu3.1   libmono-security2.0-cil         1.2.6+dfsg-6ubuntu3.1   libmono-system-web1.0-cil       1.2.6+dfsg-6ubuntu3.1   libmono-system-web2.0-cil       1.2.6+dfsg-6ubuntu3.1  Ubuntu 8.10:   libmono-security1.0-cil         1.9.1+dfsg-4ubuntu2.1   libmono-security2.0-cil         1.9.1+dfsg-4ubuntu2.1   libmono-system-web1.0-cil       1.9.1+dfsg-4ubuntu2.1   libmono-system-web2.0-cil       1.9.1+dfsg-4ubuntu2.1  Ubuntu 9.04:   libmono-security1.0-cil         2.0.1-4ubuntu0.1   libmono-security2.0-cil         2.0.1-4ubuntu0.1   libmono-system-web1.0-cil       2.0.1-4ubuntu0.1   libmono-system-web2.0-cil       2.0.1-4ubuntu0.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that the XML HMAC signature system did not correctly check certain lengths. If an attacker sent a truncated HMAC, it could bypass authentication, leading to potential privilege escalation. (CVE-2009-0217)  It was discovered that Mono did not properly escape certain attributes in the ASP.net class libraries which could result in browsers becoming vulnerable to cross-site scripting attacks when processing the output. With cross-site scripting vulnerabilities, if a user were tricked into viewing server output during a crafted server request, a remote attacker could exploit this to modify the contents, or steal confidential data (such as passwords), within the same domain. This issue only affected Ubuntu 8.04 LTS. (CVE-2008-3422)  It was discovered that Mono did not properly filter CRLF injections in the query string. If a user were tricked into viewing server output during a crafted server request, a remote attacker could exploit this to modify the contents, steal confidential data (such as passwords), or perform cross-site request forgeries. This issue only affected Ubuntu 8.04 LTS. (CVE-2008-3906)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-826-1)

---

