---
title: "USN-612-9: openssl-blacklist update"
date: 2008-06-12
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-06-12
Description: 
 ===========================================================  Ubuntu Security Notice USN-612-9              June 12, 2008 openssl-blacklist update [http://www.ubuntu.com/usn/usn-612-1](http://www.ubuntu.com/usn/usn-612-1) [http://www.ubuntu.com/usn/usn-612-3](http://www.ubuntu.com/usn/usn-612-3) [http://www.ubuntu.com/usn/usn-612-8](http://www.ubuntu.com/usn/usn-612-8) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   openssl-blacklist               0.3.3+0.4-0ubuntu0.6.06.1   openssl-blacklist-extra         0.3.3+0.4-0ubuntu0.6.06.1  Ubuntu 7.04:   openssl-blacklist               0.3.3+0.4-0ubuntu0.7.04.1   openssl-blacklist-extra         0.3.3+0.4-0ubuntu0.7.04.1  Ubuntu 7.10:   openssl-blacklist               0.3.3+0.4-0ubuntu0.7.10.1   openssl-blacklist-extra         0.3.3+0.4-0ubuntu0.7.10.1  Ubuntu 8.04 LTS:   openssl-blacklist               0.3.3+0.4-0ubuntu0.8.04.1   openssl-blacklist-extra         0.3.3+0.4-0ubuntu0.8.04.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  USN-612-3 addressed a weakness in OpenSSL certificate and key generation in OpenVPN by introducing openssl-blacklist to aid in detecting vulnerable private keys. This update enhances the openssl-vulnkey tool to check Certificate Signing Requests, accept input from STDIN, and check moduli without a certificate.  It was also discovered that additional moduli are vulnerable if generated with OpenSSL 0.9.8g or higher. While it is believed that there are few of these vulnerable moduli in use, this update includes updated RSA-1024 and RSA-2048 blacklists. RSA-512 blacklists are also included in the new openssl-blacklist-extra package.  You can check for weak SSL/TLS certificates by installing openssl-blacklist via your package manager, and using the openssl-vulnkey command.  $ openssl-vulnkey /path/to/certificate_or_key $ cat /path/to/certificate_or_key | openssl-vulnkey -  You can also check if a modulus is vulnerable by specifying the modulus and number of bits.  $ openssl-vulnkey -b bits -m modulus  These commands can be used on public certificates, requests, and private keys for any X.509 certificate, CSR, or RSA key, including ones for web servers, mail servers, OpenVPN, and others. If in doubt, destroy the certificate and key and generate new ones. Please consult the documentation for your software when recreating SSL/TLS certificates. Also, if certificates have been generated for use on other systems, they must be found and replaced as well.  Original advisory details:  A weakness has been discovered in the random number generator used  by OpenSSL on Debian and Ubuntu systems. As a result of this  weakness, certain encryption keys are much more common than they  should be, such that an attacker could guess the key through a  brute-force attack given minimal knowledge of the system. This  particularly affects the use of encryption keys in OpenSSH, OpenVPN  and SSL certificates. 





[More...](http://www.ubuntu.com/usn/usn-612-9)

---

