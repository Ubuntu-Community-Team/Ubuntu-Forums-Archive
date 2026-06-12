---
title: "USN-726-2: curl regression"
date: 2009-03-04
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-03-04
Description: 
=========================================================== Ubuntu Security Notice USN-726-2             March 04, 2009 curl regression [https://launchpad.net/bugs/337501](https://launchpad.net/bugs/337501) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.10:   libcurl3                        7.18.2-1ubuntu4.3   libcurl3-gnutls                 7.18.2-1ubuntu4.3  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  USN-726-1 fixed a vulnerability in curl. Due to an incomplete fix, a regression was introduced in Ubuntu 8.10 that caused certain types of URLs to fail. This update fixes the problem. We apologize for the inconvenience.  Original advisory details:   It was discovered that curl did not enforce any restrictions when following  URL redirects. If a user or automated system were tricked into opening a URL to  an untrusted server, an attacker could use redirects to gain access to abitrary  files. This update changes curl behavior to prevent following "file" URLs after  a redirect.





[More...](http://www.ubuntu.com/usn/USN-726-2)

---

