---
title: "USN-663-1: system-tools-backends regression"
date: 2008-11-05
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-11-05
Description: 
 =========================================================== Ubuntu Security Notice USN-663-1          November 05, 2008 system-tools-backends regression [https://launchpad.net/bugs/287134](https://launchpad.net/bugs/287134) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.10:   system-tools-backends           2.6.0-1ubuntu1.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that passwords changed (or new users created) via the "Users and Groups" tool were created with 3DES hashing.  This reduced the security of stored user passwords, and was a regression from the correct MD5 hashing.  This update fixes the problem; future password changes will correct the hashing used.  We apologize for the inconvenience. 





[More...](http://www.ubuntu.com/usn/usn-663-1)

---

