---
title: "[USN-9-1] tetex-bin vulnerabilities"
date: 2004-10-28
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2004-10-28
===========================================================
Ubuntu Security Notice USN-9-1             October 27, 2004
tetex-bin vulnerabilities
CAN-2004-0888
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)

The following packages are affected:

tetex-bin

The problem can be corrected by upgrading the affected package to
version 2.0.2-21ubuntu0.1. In general, a standard system upgrade is
sufficient to effect the necessary changes.

Details follow:

Chris Evans and Marcus Meissner recently discovered several integer
overflow vulnerabilities in xpdf, a viewer for PDF files. Because
tetex-bin contains xpdf code, it is also affected. These
vulnerabilities could be exploited by an attacker providing a
specially crafted TeX, LaTeX, or PDF file. Processing such a file with
pdflatex could result in abnormal program termination or the execution
of program code supplied by the attacker.

This bug could be exploited to gain the privileges of the user
invoking pdflatex.

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/tetex-bin_2.0.2-21ubuntu0.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/tetex-bin_2.0.2-21ubuntu0.1.diff.gz)
      Size/MD5:   109940 a991d6b8fddbd78ad31ac5a46d79ed01
    [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/tetex-bin_2.0.2-21ubuntu0.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/tetex-bin_2.0.2-21ubuntu0.1.dsc)
      Size/MD5:     1062 4322b3e9094b0e44f22265593564f139
    [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/tetex-bin_2.0.2.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/tetex-bin_2.0.2.orig.tar.gz)
      Size/MD5: 11677169 8f02d5940bf02072ce5fe05429c90e63

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea-dev_2.0.2-21ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea-dev_2.0.2-21ubuntu0.1_amd64.deb)
      Size/MD5:    72748 26a4fc82ba25ac5ca940a737041453b1
    [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea3_2.0.2-21ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea3_2.0.2-21ubuntu0.1_amd64.deb)
      Size/MD5:    59692 73a8d7170b832199fd8d30c9ae97b4f1
    [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/tetex-bin_2.0.2-21ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/tetex-bin_2.0.2-21ubuntu0.1_amd64.deb)
      Size/MD5:  4327570 e2844193fedd86bcd8c47648b312cf34

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea-dev_2.0.2-21ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea-dev_2.0.2-21ubuntu0.1_i386.deb)
      Size/MD5:    64828 d6e40f6dde8b8a0de67a3e09e996e9ae
    [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea3_2.0.2-21ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea3_2.0.2-21ubuntu0.1_i386.deb)
      Size/MD5:    56096 c2afaf377ee1164b0c7ce88b0576af08
    [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/tetex-bin_2.0.2-21ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/tetex-bin_2.0.2-21ubuntu0.1_i386.deb)
      Size/MD5:  3811926 21d7b11851a2c74241a4b595d21ef561

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea-dev_2.0.2-21ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea-dev_2.0.2-21ubuntu0.1_powerpc.deb)
      Size/MD5:    74898 3b5ced3706ba6bf1618cf128096e3dfc
    [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea3_2.0.2-21ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea3_2.0.2-21ubuntu0.1_powerpc.deb)
      Size/MD5:    61010 f1c488019b4869fd5f417f5b11661569
    [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/tetex-bin_2.0.2-21ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/tetex-bin_2.0.2-21ubuntu0.1_powerpc.deb)
      Size/MD5:  4349926 4a0aebf5a1c3a1ad0c6b8d6ab6a39e04

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.4 (GNU/Linux)

iD8DBQFBgIzvDecnbV4Fd/IRAmYaAKCOqeKaiXfBM8WSZMfsUB3/R3BJHACdGm96
slvU21a8xWVgtdm6j/n3owE=
=WF2I
-----END PGP SIGNATURE-----

---

