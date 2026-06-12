---
title: "USN-734-1: FFmpeg vulnerabilities"
date: 2009-03-16
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-03-16
Referenced CVEs: 
CVE-2008-4610, CVE-2008-4866, CVE-2008-4867, CVE-2009-0385


Description: 
=========================================================== Ubuntu Security Notice USN-734-1             March 16, 2009 ffmpeg, ffmpeg-debian vulnerabilities CVE-2008-4610, CVE-2008-4866, CVE-2008-4867, CVE-2009-0385 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 7.10:   libavcodec1d                    3:0.cvs20070307-5ubuntu4.2   libavformat1d                   3:0.cvs20070307-5ubuntu4.2  Ubuntu 8.04 LTS:   libavcodec1d                    3:0.cvs20070307-5ubuntu7.3   libavformat1d                   3:0.cvs20070307-5ubuntu7.3  Ubuntu 8.10:   libavcodec51                    3:0.svn20080206-12ubuntu3.1   libavformat52                   3:0.svn20080206-12ubuntu3.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that FFmpeg did not correctly handle certain malformed Ogg Media (OGM) files. If a user were tricked into opening a crafted Ogg Media file, an attacker could cause the application using FFmpeg to crash, leading to a denial of service. (CVE-2008-4610)  It was discovered that FFmpeg did not correctly handle certain parameters when creating DTS streams. If a user were tricked into processing certain commands, an attacker could cause a denial of service via application crash, or possibly execute arbitrary code with the privileges of the user invoking the program. This issue only affected Ubuntu 8.10. (CVE-2008-4866)  It was discovered that FFmpeg did not correctly handle certain malformed DTS Coherent Acoustics (DCA) files. If a user were tricked into opening a crafted DCA file, an attacker could cause a denial of service via application crash, or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-4867)  It was discovered that FFmpeg did not correctly handle certain malformed 4X movie (4xm) files. If a user were tricked into opening a crafted 4xm file, an attacker could execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-0385)





[More...](http://www.ubuntu.com/usn/USN-734-1)

---

