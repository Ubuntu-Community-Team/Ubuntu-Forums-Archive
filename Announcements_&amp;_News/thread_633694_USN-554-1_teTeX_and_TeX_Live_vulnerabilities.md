---
title: "USN-554-1: teTeX and TeX Live vulnerabilities"
date: 2007-12-06
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-12-06
Referenced CVEs:
CVE-2007-5935 CVE-2007-5936 CVE-2007-5937


Description:
===========================================================Ubuntu Security Notice USN-554-1          December 06, 2007tetex-bin, texlive-bin vulnerabilitiesCVE-2007-5935, CVE-2007-5936, CVE-2007-5937===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSUbuntu 6.10Ubuntu 7.04Ubuntu 7.10This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  tetex-bin                       3.0-13ubuntu6.1Ubuntu 6.10:  tetex-bin                       3.0-17ubuntu2.1Ubuntu 7.04:  tetex-bin                       3.0-27ubuntu1.2Ubuntu 7.10:  texlive-extra-utils             2007-12ubuntu3.1In general, a standard system upgrade is sufficient to effect thenecessary changes.Details follow:Bastien Roucaries discovered that dvips as included in tetex-binand texlive-bin did not properly perform bounds checking. If auser or automated system were tricked into processing a speciallycrafted dvi file, dvips could be made to crash and execute code asthe user invoking the program. (CVE-2007-5935)Joachim Schrod discovered that the dviljk utilities createdtemporary files in an insecure way. Local users could exploit arace condition to create or overwrite files with the privileges ofthe user invoking the program. (CVE-2007-5936)Joachim Schrod discovered that the dviljk utilities did notperform bounds checking in many instances. If a user or automatedsystem were tricked into processing a specially crafted dvi file,the dviljk utilities could be made to crash and execute code asthe user invoking the program. (CVE-2007-5937)





[More...](http://www.ubuntu.com/usn/USN-554-1)

---

