---
title: "USN-550-2: Cairo regression"
date: 2007-12-10
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-12-10
Description:
 ===========================================================  Ubuntu Security Notice USN-550-2          December 10, 2007 libcairo regression [https://launchpad.net/bugs/NNNNNN](https://launchpad.net/bugs/NNNNNN) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 7.04:   libcairo2                       1.4.2-0ubuntu1.2  Ubuntu 7.10:   libcairo2                       1.4.10-1ubuntu4.2  After a standard system upgrade you need to restart your session to effect the necessary changes.  Details follow:  USN-550-1 fixed vulnerabilities in Cairo.  The upstream fixes were incomplete, and under certain situations, applications using Cairo would crash with a floating point error.  This update fixes the problem.  We apologize for the inconvenience.  Original advisory details:   Peter Valchev discovered that Cairo did not correctly decode PNG image data.  By tricking a user or automated system into processing a specially crafted  PNG with Cairo, a remote attacker could execute arbitrary code with user  privileges. 





[More...](http://www.ubuntu.com/usn/usn-550-2)

---

