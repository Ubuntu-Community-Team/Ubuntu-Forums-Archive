---
title: "USN-612-8: openssl-blacklist update"
date: 2008-05-21
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-05-21
Description: 
 ===========================================================  Ubuntu Security Notice USN-612-8               May 21, 2008 openssl-blacklist update [http://www.ubuntu.com/usn/usn-612-1](http://www.ubuntu.com/usn/usn-612-1) [http://www.ubuntu.com/usn/usn-612-3](http://www.ubuntu.com/usn/usn-612-3) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   openssl-blacklist               0.1-0ubuntu0.6.06.1  Ubuntu 7.04:   openssl-blacklist               0.1-0ubuntu0.7.04.4  Ubuntu 7.10:   openssl-blacklist               0.1-0ubuntu0.7.10.4  Ubuntu 8.04 LTS:   openssl-blacklist               0.1-0ubuntu0.8.04.4  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  USN-612-3 addressed a weakness in OpenSSL certificate and key generation in OpenVPN by introducing openssl-blacklist to aid in detecting vulnerable private keys. This update enhances the openssl-vulnkey tool to check X.509 certificates as well, and provides the corresponding update for Ubuntu 6.06. While the OpenSSL in Ubuntu 6.06 was not vulnerable, openssl-blacklist is now provided for Ubuntu 6.06 for checking certificates and keys that may have been imported on these systems.  This update also includes the complete RSA-1024 and RSA-2048 blacklists for all Ubuntu architectures, as well as support for other future blacklists for non-standard bit lengths.  You can check for weak SSL/TLS certificates by installing openssl-blacklist via your package manager, and using the openssl-vulnkey command.  $ openssl-vulnkey /path/to/certificate_or_key  This command can be used on public certificates and private keys for any X.509 certificate or RSA key, including ones for web servers, mail servers, OpenVPN, and others. If in doubt, destroy the certificate and key and generate new ones. Please consult the documentation for your software when recreating SSL/TLS certificates. Also, if certificates have been generated for use on other systems, they must be found and replaced as well.  Original advisory details:   A weakness has been discovered in the random number generator used  by OpenSSL on Debian and Ubuntu systems.  As a result of this  weakness, certain encryption keys are much more common than they  should be, such that an attacker could guess the key through a  brute-force attack given minimal knowledge of the system.  This  particularly affects the use of encryption keys in OpenSSH, OpenVPN  and SSL certificates. 





[More...](http://www.ubuntu.com/usn/usn-612-8)

---

