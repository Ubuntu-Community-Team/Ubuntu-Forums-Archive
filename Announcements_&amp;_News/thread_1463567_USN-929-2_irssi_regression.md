---
title: "USN-929-2: irssi regression"
date: 2010-04-27
forum: Announcements &amp; News
---

### Post by rss-bot on 2010-04-27
Description: 
                                        =========================================================== Ubuntu Security Notice USN-929-2             April 20, 2010 irssi regression [https://launchpad.net/bugs/565182](https://launchpad.net/bugs/565182) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04 Ubuntu 9.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   irssi                           0.8.12-3ubuntu3.3  Ubuntu 8.10:   irssi                           0.8.12-4ubuntu2.3  Ubuntu 9.04:   irssi                           0.8.12-6ubuntu1.3  Ubuntu 9.10:   irssi                           0.8.14-1ubuntu1.2  After a standard system upgrade you need to restart irssi to effect the necessary changes.  Details follow:  USN-929-1 fixed vulnerabilities in irssi. The upstream changes introduced a regression when using irssi with SSL and an IRC proxy. This update fixes the problem.  We apologize for the inconvenience.  Original advisory details:   It was discovered that irssi did not perform certificate host validation  when using SSL connections. An attacker could exploit this to perform a man  in the middle attack to view sensitive information or alter encrypted  communications. (CVE-2010-1155)    Aurelien Delaitre discovered that irssi could be made to dereference a NULL  pointer when a user left the channel. A remote attacker could cause a  denial of service via application crash. (CVE-2010-1156)    This update also adds SSLv3 and TLSv1 support, while disabling the old,  insecure SSLv2 protocol. 
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-929-2)

---

