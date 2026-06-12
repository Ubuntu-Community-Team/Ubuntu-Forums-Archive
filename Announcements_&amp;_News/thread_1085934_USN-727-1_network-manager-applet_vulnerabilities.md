---
title: "USN-727-1: network-manager-applet vulnerabilities"
date: 2009-03-03
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-03-03
Referenced CVEs: 
CVE-2009-0365, CVE-2009-0578


Description: 
=========================================================== Ubuntu Security Notice USN-727-1             March 03, 2009 network-manager-applet vulnerabilities CVE-2009-0365, CVE-2009-0578 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 7.10:   network-manager-gnome           0.6.5-0ubuntu11~7.10.1  Ubuntu 8.04 LTS:   network-manager-gnome           0.6.6-0ubuntu3.1  Ubuntu 8.10:   network-manager-gnome           0.7~~svn20081020t000444-0ubuntu1.8.10.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that network-manager-applet did not properly enforce permissions when responding to dbus requests. A local user could perform dbus queries to view other users' network connection passwords and pre-shared keys. (CVE-2009-0365)  It was discovered that network-manager-applet did not properly enforce permissions when responding to dbus modify and delete requests. A local user could use dbus to modify or delete other users' network connections. This issue only applied to Ubuntu 8.10. (CVE-2009-0578)





[More...](http://www.ubuntu.com/usn/USN-727-1)

---

