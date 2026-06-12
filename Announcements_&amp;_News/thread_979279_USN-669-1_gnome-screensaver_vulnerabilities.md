---
title: "USN-669-1: gnome-screensaver vulnerabilities"
date: 2008-11-11
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-11-11
Referenced CVEs: 
CVE-2007-6389, CVE-2008-0887


Description: 
=========================================================== Ubuntu Security Notice USN-669-1          November 11, 2008 gnome-screensaver vulnerabilities CVE-2007-6389, CVE-2008-0887 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   gnome-screensaver               2.14.3-0ubuntu1.1  Ubuntu 7.10:   gnome-screensaver               2.20.0-0ubuntu4.3  After a standard system upgrade you need to restart all user sessions on your computer to effect the necessary changes.  Details follow:  It was discovered that the notify feature in gnome-screensaver could let a local attacker read the clipboard contents of a locked session by using Ctrl-V. (CVE-2007-6389)  Alan Matsuoka discovered that gnome-screensaver did not properly handle network outages when using a remote authentication service. During a network interruption, or by disconnecting the network cable, a local attacker could gain access to locked sessions. (CVE-2008-0887)





[More...](http://www.ubuntu.com/usn/USN-669-1)

---

