---
title: "[SOLVED] [USN-43-1] groff utility vulnerabilities"
date: 2004-12-20
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2004-12-20
===========================================================
Ubuntu Security Notice USN-43-1		  December 20, 2004
groff vulnerabilities
[http://bugs.debian.org/286371](http://bugs.debian.org/286371), 
[http://bugs.debian.org/286372](http://bugs.debian.org/286372)
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)

The following packages are affected:

groff

The problem can be corrected by upgrading the affected package to
version 1.18.1.1-1ubuntu0.2. In general, a standard system upgrade is
sufficient to effect the necessary changes.

Details follow:

Javier Fernández-Sanguino Peña discovered that the auxiliary scripts
"eqn2graph" and "pic2graph" created temporary files in an insecure
way, which allowed exploitation of a race condition to create or
overwrite files with the privileges of the user invoking the program.

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff_1.18.1.1-1ubuntu0.2.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff_1.18.1.1-1ubuntu0.2.diff.gz)
      Size/MD5:   122991 0d247788b6e83f87718c996f0fd05e41
    [http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff_1.18.1.1-1ubuntu0.2.dsc](http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff_1.18.1.1-1ubuntu0.2.dsc)
      Size/MD5:      715 92ca1b33ea0907aa6d4eda3db4930c51
    [http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff_1.18.1.1.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff_1.18.1.1.orig.tar.gz)
      Size/MD5:  2260623 511dbd64b67548c99805f1521f82cc5e

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff-base_1.18.1.1-1ubuntu0.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff-base_1.18.1.1-1ubuntu0.2_amd64.deb)
      Size/MD5:   856342 920534f39127c7216e62b1122fbe3c18
    [http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff_1.18.1.1-1ubuntu0.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff_1.18.1.1-1ubuntu0.2_amd64.deb)
      Size/MD5:  1890064 f012658b3b6a9aaf9151dd9aa34cc3d1

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff-base_1.18.1.1-1ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff-base_1.18.1.1-1ubuntu0.2_i386.deb)
      Size/MD5:   807612 52dc8a36fd9838ff546a2b09e48f6b12
    [http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff_1.18.1.1-1ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff_1.18.1.1-1ubuntu0.2_i386.deb)
      Size/MD5:  1843076 677a86c7457eed2880100c122bcc75fd

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff-base_1.18.1.1-1ubuntu0.2_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff-base_1.18.1.1-1ubuntu0.2_powerpc.deb)
      Size/MD5:   860678 b2a2a921dcdbb0acc520c7de969a5104
    [http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff_1.18.1.1-1ubuntu0.2_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/g/groff/groff_1.18.1.1-1ubuntu0.2_powerpc.deb)
      Size/MD5:  1885062 e97f22decb7cc85fb32d76bc29f6d89a

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.4 (GNU/Linux)

iD8DBQFBxxiYDecnbV4Fd/IRAtl6AJ47PPzEOTxucAT3jW9ufaNsj3ez9gCgvMwR
tjn88AQCl4L+DRGTMxojteQ=
=r5vg
-----END PGP SIGNATURE-----

---

