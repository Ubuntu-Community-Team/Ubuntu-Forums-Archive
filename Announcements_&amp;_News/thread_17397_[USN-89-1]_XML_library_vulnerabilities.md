---
title: "[USN-89-1] XML library vulnerabilities"
date: 2005-02-28
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-02-28
===========================================================
Ubuntu Security Notice USN-89-1		  February 28, 2005
libxml vulnerabilities
CAN-2004-0989
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)

The following packages are affected:

libxml1

The problem can be corrected by upgrading the affected package to
version 1:1.8.17-8ubuntu0.1.  In general, a standard system upgrade is
sufficient to effect the necessary changes.

Details follow:

Several buffer overflows have been discovered in libxml's FTP
connection and DNS resolution functions. Supplying very long FTP URLs
or IP addresses might result in execution of arbitrary code with the
privileges of the process using libxml.

This does not affect the core XML parsing code, which is what the
majority of programs use this library for.

Note: The same vulnerability was already fixed for libxml2 in
USN-10-1.

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml_1.8.17-8ubuntu0.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml_1.8.17-8ubuntu0.1.diff.gz)
      Size/MD5:   361144 49c17811be2abc30c48984e0f46454fb
    [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml_1.8.17-8ubuntu0.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml_1.8.17-8ubuntu0.1.dsc)
      Size/MD5:      756 5d9e3b59a2d624d52af231926a84fb1d
    [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml_1.8.17.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml_1.8.17.orig.tar.gz)
      Size/MD5:  1016403 b8f01e43e1e03dec37dfd6b4507a9568

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml-dev_1.8.17-8ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml-dev_1.8.17-8ubuntu0.1_amd64.deb)
      Size/MD5:   385860 672acd61cde9389539ea2e8d68a1d2db
    [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml1_1.8.17-8ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml1_1.8.17-8ubuntu0.1_amd64.deb)
      Size/MD5:   225922 e1f0cdc93c32b6bd256070dc45d5e2a7

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml-dev_1.8.17-8ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml-dev_1.8.17-8ubuntu0.1_i386.deb)
      Size/MD5:   361434 41037748a8cb40a6bd26b0d0d5ee3387
    [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml1_1.8.17-8ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml1_1.8.17-8ubuntu0.1_i386.deb)
      Size/MD5:   212158 7f149fcc590aa2162810fdae5a47cd29

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml-dev_1.8.17-8ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml-dev_1.8.17-8ubuntu0.1_powerpc.deb)
      Size/MD5:   392636 b445671f31603b7e12b8c47fd7ea6697
    [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml1_1.8.17-8ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml/libxml1_1.8.17-8ubuntu0.1_powerpc.deb)
      Size/MD5:   220004 e3cd12326fae6972a44ac59a8af97697

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.5 (GNU/Linux)

iD8DBQFCIyuuDecnbV4Fd/IRAiqWAJ9B8rqHugwK8YY4Tcyq+fZf01VvzwCg4h2Z
dUXCF7eIB5osxTxCsl/twR4=
=7iTF
-----END PGP SIGNATURE-----

---

