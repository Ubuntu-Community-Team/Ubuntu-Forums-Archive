---
title: "USN-612-7: OpenSSH update"
date: 2008-05-20
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-05-20
Referenced CVEs: 
CVE-2008-0166


Description: 
 ===========================================================  Ubuntu Security Notice USN-612-7               May 20, 2008 openssh update CVE-2008-0166 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   openssh-server                  1:4.2p1-7ubuntu3.4  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  USN-612-2 introduced protections for OpenSSH, related to the OpenSSL vulnerabilities addressed by USN-612-1.  This update provides the corresponding updates for OpenSSH in Ubuntu 6.06 LTS.  While the OpenSSL in Ubuntu 6.06 is not vulnerable, this update will block weak keys generated on systems that may have been affected themselves.  Original advisory details:   A weakness has been discovered in the random number generator used  by OpenSSL on Debian and Ubuntu systems.  As a result of this  weakness, certain encryption keys are much more common than they  should be, such that an attacker could guess the key through a  brute-force attack given minimal knowledge of the system.  This  particularly affects the use of encryption keys in OpenSSH, OpenVPN  and SSL certificates. 





[More...](http://www.ubuntu.com/usn/usn-612-7)

---

