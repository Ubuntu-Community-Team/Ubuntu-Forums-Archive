---
title: "USN-550-3: Cairo regression"
date: 2007-12-13
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-12-13
Description:
 ===========================================================  Ubuntu Security Notice USN-550-3          December 13, 2007 libcairo regression [https://launchpad.net/bugs/175573](https://launchpad.net/bugs/175573) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libcairo2                       1.0.4-0ubuntu1.2  Ubuntu 6.10:   libcairo2                       1.2.4-1ubuntu2.2  Ubuntu 7.04:   libcairo2                       1.4.2-0ubuntu1.3  Ubuntu 7.10:   libcairo2                       1.4.10-1ubuntu4.4  After a standard system upgrade you need to restart your session to effect the necessary changes.  Details follow:  USN-550-1 fixed vulnerabilities in Cairo.  A bug in font glyph rendering was uncovered as a result of the new memory allocation routines.  In certain situations, fonts containing characters with no width or height would not render any more.  This update fixes the problem.  We apologize for the inconvenience.  Original advisory details:   Peter Valchev discovered that Cairo did not correctly decode PNG image data.  By tricking a user or automated system into processing a specially crafted  PNG with Cairo, a remote attacker could execute arbitrary code with user  privileges. 





[More...](http://www.ubuntu.com/usn/usn-550-3)

---

