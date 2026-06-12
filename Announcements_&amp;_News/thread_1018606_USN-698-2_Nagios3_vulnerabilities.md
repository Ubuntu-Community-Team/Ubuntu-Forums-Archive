---
title: "USN-698-2: Nagios3 vulnerabilities"
date: 2008-12-22
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-12-22
Referenced CVEs: 
CVE-2008-5027, CVE-2008-5028


Description: 
=========================================================== Ubuntu Security Notice USN-698-2          December 22, 2008 nagios3 vulnerabilities CVE-2008-5027, CVE-2008-5028 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.10:   nagios3                         3.0.2-1ubuntu1.1  After a standard system upgrade you need to restart Nagios to effect the necessary changes.  Details follow:  It was discovered that Nagios was vulnerable to a Cross-site request forgery (CSRF) vulnerability. If an authenticated nagios user were tricked into clicking a link on a specially crafted web page, an attacker could trigger commands to be processed by Nagios and execute arbitrary programs. This update alters Nagios behaviour by disabling submission of CMD_CHANGE commands. (CVE-2008-5028)  It was discovered that Nagios did not properly parse commands submitted using the web interface. An authenticated user could use a custom form or a browser addon to bypass security restrictions and submit unauthorized commands. (CVE-2008-5027)





[More...](http://www.ubuntu.com/usn/USN-698-2)

---

