---
title: "vulnerabilities: Thunderbird vulnerabilities"
date: 2007-08-27
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-08-27
Referenced CVEs:
CVE-2007-3670, CVE-2007-3734, CVE-2007-3735, CVE-2007-3844, CVE-2007-3845


Description:
 ----- Forwarded message from Kees Cook  -----  From: Kees Cook  To: [email]security@ubuntu.com[/email] Envelope-To: [email]kees@outflux.net[/email] Subject: [USN-503-1] Thunderbird vulnerabilities  ===========================================================  Ubuntu Security Notice USN-503-1            August 24, 2007 mozilla-thunderbird vulnerabilities CVE-2007-3670, CVE-2007-3734, CVE-2007-3735, CVE-2007-3844, CVE-2007-3845 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   mozilla-thunderbird             1.5.0.13-0ubuntu0.6.06  Ubuntu 6.10:   mozilla-thunderbird             1.5.0.13-0ubuntu0.6.10  Ubuntu 7.04:   mozilla-thunderbird             1.5.0.13-0ubuntu0.7.04  After a standard system upgrade you need to restart Thunderbird to effect the necessary changes.  Details follow:  Various flaws were discovered in the layout and JavaScript engines. By tricking a user into opening a malicious email, an attacker could execute arbitrary code with the user's privileges. Please note that JavaScript is disabled by default for emails, and it is not recommended to enable it. (CVE-2007-3734, CVE-2007-3735, CVE-2007-3844)  Jesper Johansson discovered that spaces and double-quotes were not correctly handled when launching external programs. In rare configurations, after tricking a user into opening a malicious email, an attacker could execute helpers with arbitrary arguments with the user's privileges. (CVE-2007-3670, CVE-2007-3845) 





[More...](http://www.ubuntu.com/usn/vulnerabilities)

---

