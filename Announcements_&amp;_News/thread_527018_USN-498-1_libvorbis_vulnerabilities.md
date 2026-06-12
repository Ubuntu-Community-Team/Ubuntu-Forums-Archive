---
title: "USN-498-1: libvorbis vulnerabilities"
date: 2007-08-16
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-08-16
Referenced CVEs:
CVE-2007-3106, CVE-2007-4029


Description:
 ===========================================================  Ubuntu Security Notice USN-498-1            August 16, 2007 libvorbis vulnerabilities CVE-2007-3106, CVE-2007-4029 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libvorbis0a                              1.1.2-0ubuntu2.2  Ubuntu 6.10:   libvorbis0a                              1.1.2-1ubuntu1.2  Ubuntu 7.04:   libvorbis0a                              1.1.2.dfsg-1.2ubuntu2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  David Thiel discovered that libvorbis did not correctly verify the size of certain headers, and did not correctly clean up a broken stream. If a user were tricked into processing a specially crafted Vorbis stream, a remote attacker could execute arbitrary code with the user's privileges. 





[More...](http://www.ubuntu.com/usn/usn-498-1)

---

