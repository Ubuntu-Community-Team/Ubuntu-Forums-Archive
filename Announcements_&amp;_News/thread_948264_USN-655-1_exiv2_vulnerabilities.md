---
title: "USN-655-1: exiv2 vulnerabilities"
date: 2008-10-15
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-10-15
Referenced CVEs: 
CVE-2007-6353, CVE-2008-2696


Description: 
===========================================================Ubuntu Security Notice USN-655-1           October 15, 2008exiv2 vulnerabilitiesCVE-2007-6353, CVE-2008-2696===========================================================A security issue affects the following Ubuntu releases:Ubuntu 7.04Ubuntu 7.10Ubuntu 8.04 LTSThis advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 7.04:  libexiv2-0.12                   0.12-0ubuntu2.1Ubuntu 7.10:  libexiv2-0                      0.15-1ubuntu2.1Ubuntu 8.04 LTS:  libexiv2-2                      0.16-3ubuntu1.1After a standard system upgrade you need to restart your session to effectthe necessary changes.Details follow:Meder Kydyraliev discovered that exiv2 did not correctly handle certainEXIF headers. If a user or automated system were tricked into processinga specially crafted image, a remote attacker could cause the applicationlinked against libexiv2 to crash, leading to a denial of service, orpossibly executing arbitrary code with user privileges. (CVE-2007-6353)Joakim Bildrulle discovered that exiv2 did not correctly handle Nikonlens EXIF information.  If a user or automated system were tricked intoprocessing a specially crafted image, a remote attacker could cause theapplication linked against libexiv2 to crash, leading to a denial ofservice. (CVE-2008-2696)





[More...](http://www.ubuntu.com/usn/usn-655-1)

---

