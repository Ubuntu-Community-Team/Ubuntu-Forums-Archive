---
title: "USN-931-2: FFmpeg regression"
date: 2010-04-27
forum: Announcements &amp; News
---

### Post by rss-bot on 2010-04-27
Description: 
                                       =========================================================== Ubuntu Security Notice USN-931-2             April 26, 2010 ffmpeg, ffmpeg-debian regression [https://launchpad.net/bugs/567913](https://launchpad.net/bugs/567913) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04 Ubuntu 9.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   libavcodec1d                    3:0.cvs20070307-5ubuntu7.5   libavformat1d                   3:0.cvs20070307-5ubuntu7.5  Ubuntu 8.10:   libavcodec51                    3:0.svn20080206-12ubuntu3.3   libavformat52                   3:0.svn20080206-12ubuntu3.3  Ubuntu 9.04:   libavcodec52                    3:0.svn20090303-1ubuntu6.2   libavformat52                   3:0.svn20090303-1ubuntu6.2  Ubuntu 9.10:   libavcodec52                    4:0.5+svn20090706-2ubuntu2.2   libavformat52                   4:0.5+svn20090706-2ubuntu2.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  USN-931-1 fixed vulnerabilities in FFmpeg. The update introduced a regression when trying to play certain multimedia files. This update fixes the problem.  We apologize for the inconvenience.  Original advisory details:   It was discovered that FFmpeg contained multiple security issues when  handling certain multimedia files. If a user were tricked into opening a  crafted multimedia file, an attacker could cause a denial of service via  application crash, or possibly execute arbitrary code with the privileges  of the user invoking the program.
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-931-2)

---

