---
title: "USN-678-2: GnuTLS regression"
date: 2008-12-10
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-12-10
Description: 
 =========================================================== Ubuntu Security Notice USN-678-2          December 09, 2008 gnutls12, gnutls13, gnutls26 regression [https://launchpad.net/bugs/305264](https://launchpad.net/bugs/305264) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libgnutls12                     1.2.9-2ubuntu1.4  Ubuntu 7.10:   libgnutls13                     1.6.3-1ubuntu0.3  Ubuntu 8.04 LTS:   libgnutls13                     2.0.4-1ubuntu2.3  Ubuntu 8.10:   libgnutls26                     2.4.1-1ubuntu0.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  USN-678-1 fixed a vulnerability in GnuTLS. The upstream patch introduced a regression when validating certain certificate chains that would report valid certificates as untrusted. This update fixes the problem.  We apologize for the inconvenience.  Original advisory details:   Martin von Gagern discovered that GnuTLS did not properly verify certificate  chains when the last certificate in the chain was self-signed. If a remote  attacker were able to perform a man-in-the-middle attack, this flaw could be  exploited to view sensitive information. (CVE-2008-4989) 





[More...](http://www.ubuntu.com/usn/usn-678-2)

---

