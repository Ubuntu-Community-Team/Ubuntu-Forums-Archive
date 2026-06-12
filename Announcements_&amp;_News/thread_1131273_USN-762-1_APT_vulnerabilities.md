---
title: "USN-762-1: APT vulnerabilities"
date: 2009-04-20
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-04-20
Referenced CVEs: 
                                       CVE-2009-1300        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-762-1             April 20, 2009 apt vulnerabilities CVE-2009-1300, [https://launchpad.net/bugs/356012](https://launchpad.net/bugs/356012) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   apt                             0.6.43.3ubuntu3.1   apt-doc                         0.6.43.3ubuntu3.1   apt-utils                       0.6.43.3ubuntu3.1   libapt-pkg-dev                  0.6.43.3ubuntu3.1   libapt-pkg-doc                  0.6.43.3ubuntu3.1  Ubuntu 8.04 LTS:   apt                             0.7.9ubuntu17.2   apt-doc                         0.7.9ubuntu17.2   apt-transport-https             0.7.9ubuntu17.2   apt-utils                       0.7.9ubuntu17.2   libapt-pkg-dev                  0.7.9ubuntu17.2   libapt-pkg-doc                  0.7.9ubuntu17.2  Ubuntu 8.10:   apt                             0.7.14ubuntu6.1   apt-doc                         0.7.14ubuntu6.1   apt-transport-https             0.7.14ubuntu6.1   apt-utils                       0.7.14ubuntu6.1   libapt-pkg-dev                  0.7.14ubuntu6.1   libapt-pkg-doc                  0.7.14ubuntu6.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Alexandre Martani discovered that the APT daily cron script did not check the return code of the date command. If a machine is configured for automatic updates and is in a time zone where DST occurs at midnight, under certain circumstances automatic updates might not be applied and could become permanently disabled. (CVE-2009-1300)  Michael Casadevall discovered that APT did not properly verify repositories signed with a revoked or expired key. If a repository were signed with only an expired or revoked key and the signature was otherwise valid, APT would consider the repository valid. ([https://launchpad.net/bugs/356012](https://launchpad.net/bugs/356012)) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-762-1)

---

