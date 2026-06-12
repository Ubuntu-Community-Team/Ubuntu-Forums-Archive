---
title: "USN-703-1: xterm vulnerabilities"
date: 2009-01-05
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-01-05
Referenced CVEs: 
CVE-2006-7236, CVE-2008-2383


Description: 
===========================================================Ubuntu Security Notice USN-703-1           January 06, 2009xterm vulnerabilitiesCVE-2006-7236, CVE-2008-2383===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSUbuntu 7.10Ubuntu 8.04 LTSUbuntu 8.10This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  xterm                           208-3.1ubuntu3.1Ubuntu 7.10:  xterm                           229-1ubuntu0.1Ubuntu 8.04 LTS:  xterm                           229-1ubuntu1.1Ubuntu 8.10:  xterm                           235-1ubuntu1.1After a standard system upgrade you need to restart any running xterms toeffect the necessary changes.Details follow:Paul Szabo discovered that the DECRQSS escape sequences were not handledcorrectly by xterm.  Additionally, window title operations were also notsafely handled.  If a user were tricked into viewing a specially craftedseries of characters while in xterm, a remote attacker could executearbitrary commands with user privileges. (CVE-2006-7236, CVE-2008-2382)





[More...](http://www.ubuntu.com/usn/usn-703-1)

---

