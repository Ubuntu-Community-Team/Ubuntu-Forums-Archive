---
title: "USN-612-6: OpenVPN regression"
date: 2008-05-14
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-05-14
Description: 
 ===========================================================  Ubuntu Security Notice USN-612-6               May 14, 2008 openvpn regression [https://launchpad.net/bugs/230193](https://launchpad.net/bugs/230193) [https://launchpad.net/bugs/230208](https://launchpad.net/bugs/230208) [http://www.ubuntu.com/usn/usn-612-3](http://www.ubuntu.com/usn/usn-612-3) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 7.04:   openssl-blacklist               0.1-0ubuntu0.7.04.2   openvpn                         2.0.9-5ubuntu0.2  Ubuntu 7.10:   openssl-blacklist               0.1-0ubuntu0.7.10.2   openvpn                         2.0.9-8ubuntu0.2  Ubuntu 8.04 LTS:   openssl-blacklist               0.1-0ubuntu0.8.04.2   openvpn                         2.1~rc7-1ubuntu3.2  After a standard system upgrade you need to restart openvpn to effect the necessary changes.  Details follow:  USN-612-3 addressed a weakness in OpenSSL certificate and keys generation in OpenVPN by adding checks for vulnerable certificates and keys to OpenVPN. A regression was introduced in OpenVPN when using TLS and multi-client/server which caused OpenVPN to not start  when using valid SSL certificates.  It was also found that openssl-vulnkey from openssl-blacklist would fail when stderr was not available. This caused OpenVPN to fail to start when used with applications such as NetworkManager.  This update fixes these problems. We apologize for the inconvenience.  Original advisory details:   A weakness has been discovered in the random number generator used  by OpenSSL on Debian and Ubuntu systems.  As a result of this  weakness, certain encryption keys are much more common than they  should be, such that an attacker could guess the key through a  brute-force attack given minimal knowledge of the system.  This  particularly affects the use of encryption keys in OpenSSH, OpenVPN  and SSL certificates. 





[More...](http://www.ubuntu.com/usn/usn-612-6)

---

