---
title: "USN-699-1: Blender vulnerabilities"
date: 2008-12-22
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-12-22
Referenced CVEs: 
CVE-2008-1102, CVE-2008-4863


Description: 
=========================================================== Ubuntu Security Notice USN-699-1          December 22, 2008 blender vulnerabilities CVE-2008-1102, CVE-2008-4863 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   blender                         2.41-1ubuntu4.1  After a standard system upgrade you need to restart Blender to effect the necessary changes.  Details follow:  It was discovered that Blender did not correctly handle certain malformed Radiance RGBE images. If a user were tricked into opening a .blend file containing a specially crafted Radiance RGBE image, an attacker could execute arbitrary code with the user's privileges. (CVE-2008-1102)  It was discovered that Blender did not properly sanitize the Python search path. A local attacker could execute arbitrary code by inserting a specially crafted Python file in the Blender working directory. (CVE-2008-4863)





[More...](http://www.ubuntu.com/usn/USN-699-1)

---

