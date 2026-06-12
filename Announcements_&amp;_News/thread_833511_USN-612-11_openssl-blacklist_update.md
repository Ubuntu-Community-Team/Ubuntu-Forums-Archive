---
title: "USN-612-11: openssl-blacklist update"
date: 2008-06-18
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-06-18
Description: 
 ===========================================================  Ubuntu Security Notice USN-612-11              June 18, 2008 openssl-blacklist update [http://www.ubuntu.com/usn/usn-612-1](http://www.ubuntu.com/usn/usn-612-1) [http://www.ubuntu.com/usn/usn-612-3](http://www.ubuntu.com/usn/usn-612-3) [http://www.ubuntu.com/usn/usn-612-8](http://www.ubuntu.com/usn/usn-612-8) [http://www.ubuntu.com/usn/usn-612-9](http://www.ubuntu.com/usn/usn-612-9) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   openssl-blacklist               0.3.3+0.4-0ubuntu0.6.06.2   openssl-blacklist-extra         0.3.3+0.4-0ubuntu0.6.06.2  Ubuntu 7.04:   openssl-blacklist               0.3.3+0.4-0ubuntu0.7.04.2   openssl-blacklist-extra         0.3.3+0.4-0ubuntu0.7.04.2  Ubuntu 7.10:   openssl-blacklist               0.3.3+0.4-0ubuntu0.7.10.2   openssl-blacklist-extra         0.3.3+0.4-0ubuntu0.7.10.2  Ubuntu 8.04 LTS:   openssl-blacklist               0.3.3+0.4-0ubuntu0.8.04.3   openssl-blacklist-extra         0.3.3+0.4-0ubuntu0.8.04.3  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  USN-612-3 addressed a weakness in OpenSSL certificate and key generation and introduced openssl-blacklist to aid in detecting vulnerable certificates and keys. This update adds RSA-4096 blacklists to the openssl-blacklist-extra package and adjusts openssl-vulnkey to properly handle RSA-4096 and higher moduli.  Original advisory details:  A weakness has been discovered in the random number generator used  by OpenSSL on Debian and Ubuntu systems. As a result of this  weakness, certain encryption keys are much more common than they  should be, such that an attacker could guess the key through a  brute-force attack given minimal knowledge of the system. This  particularly affects the use of encryption keys in OpenSSH, OpenVPN  and SSL certificates. 





[More...](http://www.ubuntu.com/usn/usn-612-11)

---

