---
title: "USN-612-5: OpenSSH update"
date: 2008-05-14
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-05-14
Description: 
 ===========================================================  Ubuntu Security Notice USN-612-5               May 14, 2008 openssh update [https://launchpad.net/bugs/230029](https://launchpad.net/bugs/230029) [http://www.ubuntu.com/usn/usn-612-2](http://www.ubuntu.com/usn/usn-612-2) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 7.04:   openssh-client                  1:4.3p2-8ubuntu1.4   openssh-client-udeb             1:4.3p2-8ubuntu1.4  Ubuntu 7.10:   openssh-client                  1:4.6p1-5ubuntu0.5   openssh-client-udeb             1:4.6p1-5ubuntu0.5  Ubuntu 8.04 LTS:   openssh-client                  1:4.7p1-8ubuntu1.2   openssh-client-udeb             1:4.7p1-8ubuntu1.2  After performing a standard system upgrade, users are encouraged to re-run ssh-vulnkey on their systems.  Details follow:  Matt Zimmerman discovered that entries in ~/.ssh/authorized_keys with options (such as "no-port-forwarding" or forced commands) were ignored by the new ssh-vulnkey tool introduced in OpenSSH (see USN-612-2). This could cause some compromised keys not to be listed in ssh-vulnkey's output.  This update also adds more information to ssh-vulnkey's manual page.  Original advisory details:   A weakness has been discovered in the random number generator used  by OpenSSL on Debian and Ubuntu systems.  As a result of this  weakness, certain encryption keys are much more common than they  should be, such that an attacker could guess the key through a  brute-force attack given minimal knowledge of the system.  This  particularly affects the use of encryption keys in OpenSSH, OpenVPN  and SSL certificates. 





[More...](http://www.ubuntu.com/usn/usn-612-5)

---

