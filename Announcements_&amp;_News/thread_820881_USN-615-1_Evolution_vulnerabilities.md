---
title: "USN-615-1: Evolution vulnerabilities"
date: 2008-06-06
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-06-06
Referenced CVEs: 
CVE-2008-1108, CVE-2008-1109


Description: 
 ===========================================================  Ubuntu Security Notice USN-615-1              June 06, 2008 evolution vulnerabilities CVE-2008-1108, CVE-2008-1109 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   evolution                       2.6.1-0ubuntu7.4  Ubuntu 7.04:   evolution                       2.10.1-0ubuntu2.4  Ubuntu 7.10:   evolution                       2.12.1-0ubuntu1.3  Ubuntu 8.04 LTS:   evolution                       2.22.2-0ubuntu1.2  After a standard system upgrade you need to restart Evolution to effect the necessary changes.  Details follow:  Alin Rad Pop of Secunia Research discovered that Evolution did not properly validate timezone data when processing iCalendar attachments. If a user disabled the ITip Formatter plugin and viewed a crafted iCalendar attachment, an attacker could cause a denial of service or possibly execute code with user privileges. Note that the ITip Formatter plugin is enabled by default in Ubuntu. (CVE-2008-1108)  Alin Rad Pop of Secunia Research discovered that Evolution did not properly validate the DESCRIPTION field when processing iCalendar attachments. If a user were tricked into accepting a crafted iCalendar attachment and replied to it from the calendar window, an attacker code cause a denial of service or execute code with user privileges. (CVE-2008-1109)  Matej Cepl discovered that Evolution did not properly validate date fields when processing iCalendar attachments. If a user disabled the ITip Formatter plugin and viewed a crafted iCalendar attachment, an attacker could cause a denial of service. Note that the ITip Formatter plugin is enabled by default in Ubuntu. 





[More...](http://www.ubuntu.com/usn/usn-615-1)

---

