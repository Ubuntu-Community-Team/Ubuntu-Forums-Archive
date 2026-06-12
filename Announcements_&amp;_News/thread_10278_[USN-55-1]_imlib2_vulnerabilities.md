---
title: "[USN-55-1] imlib2 vulnerabilities"
date: 2005-01-06
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-01-06
===========================================================
Ubuntu Security Notice USN-55-1		   January 06, 2005
imlib2 vulnerabilities
CAN-2004-1025, CAN-2004-1026
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)

The following packages are affected:

libimlib2

The problem can be corrected by upgrading the affected package to
version 1.1.0-12ubuntu2.1. In general, a standard system upgrade is
sufficient to effect the necessary changes.

Details follow:

Recently, Pavel Kankovsky discovered several buffer overflows in imlib
which were fixed in USN-53-1. It was found that imlib2 was vulnerable
to similar issues.

If an attacker tricked a user into loading a malicious XPM or BMP
image, he could exploit this to execute arbitrary code in the context
of the user opening the image.

These vulnerabilities might also lead to privilege escalation if a
privileged server process is using this library; for example, a PHP
script on the web server which does automatic image processing might
use the php-imlib package, in which case a remote attacker could
possibly execute arbitrary code with the web server's privileges.

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/imlib2_1.1.0-12ubuntu2.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/imlib2_1.1.0-12ubuntu2.1.diff.gz)
      Size/MD5:   519125 3ece0e406b95e41d4c9399b5def6adf4
    [http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/imlib2_1.1.0-12ubuntu2.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/imlib2_1.1.0-12ubuntu2.1.dsc)
      Size/MD5:      707 4ce1ffa67516fe7b9bb5974aebd7cd0a
    [http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/imlib2_1.1.0.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/imlib2_1.1.0.orig.tar.gz)
      Size/MD5:   814851 1589ebb054da76734fe08ae570460034

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2-dev_1.1.0-12ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2-dev_1.1.0-12ubuntu2.1_amd64.deb)
      Size/MD5:   608490 298b73e1ca6d67fd67a5f1c46f4c2b17
    [http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.0-12ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.0-12ubuntu2.1_amd64.deb)
      Size/MD5:   189040 202f3d45cbdf0051d7a4b4c3a883445e

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2-dev_1.1.0-12ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2-dev_1.1.0-12ubuntu2.1_i386.deb)
      Size/MD5:   570136 3d49a87c30e254897b759ca45894d95a
    [http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.0-12ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.0-12ubuntu2.1_i386.deb)
      Size/MD5:   176266 56ffca0de995818e951b554f05dc561e

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2-dev_1.1.0-12ubuntu2.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2-dev_1.1.0-12ubuntu2.1_powerpc.deb)
      Size/MD5:   669892 f8e61e9ef1b7df0d215553ad5ff51def
    [http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.0-12ubuntu2.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.0-12ubuntu2.1_powerpc.deb)
      Size/MD5:   196958 354f393c057b2188303763dce03c474e

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.4 (GNU/Linux)

iD8DBQFB3XiEDecnbV4Fd/IRAraBAKDthEFbDgMIpczZa6F8lYUmSBmUSgCg0Hh5
2ocIZAlmQqNXQKsIFD8ir2Y=
=UQOP
-----END PGP SIGNATURE-----

---

