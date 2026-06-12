---
title: "USN-763-1: xine-lib vulnerabilities"
date: 2009-04-20
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-04-20
Referenced CVEs: 
                                       CVE-2009-0698, CVE-2009-1274        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-763-1             April 20, 2009 xine-lib vulnerabilities CVE-2009-0698, CVE-2009-1274 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libxine-main1                   1.1.1+ubuntu2-7.12  Ubuntu 8.04 LTS:   libxine1                        1.1.11.1-1ubuntu3.4  Ubuntu 8.10:   libxine1                        1.1.15-0ubuntu3.3  After a standard system upgrade you need to restart applications linked against xine-lib, such as Totem-xine and Amarok, to effect the necessary changes.  Details follow:  It was discovered that the QT demuxer in xine-lib did not correctly handle a large count value in an STTS atom, resulting in a heap-based buffer overflow. If a user or automated system were tricked into opening a specially crafted MOV file, an attacker could execute arbitrary code as the user invoking the program. (CVE-2009-1274)  USN-746-1 provided updated xine-lib packages to fix multiple security vulnerabilities. The security patch to fix CVE-2009-0698 was incomplete. This update corrects the problem.  Original advisory details:  It was discovered that the 4xm demuxer in xine-lib did not correctly  handle a large current_track value in a 4xm file, resulting in an integer  overflow. If a user or automated system were tricked into opening a  specially crafted 4xm movie file, an attacker could crash xine-lib or  possibly execute arbitrary code with the privileges of the user invoking  the program. (CVE-2009-0698)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-763-1)

---

