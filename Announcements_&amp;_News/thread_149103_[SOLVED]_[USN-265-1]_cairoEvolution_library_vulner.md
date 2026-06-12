---
title: "[SOLVED] [USN-265-1] cairo/Evolution library vulnerability"
date: 2006-03-23
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2006-03-23
===========================================================
Ubuntu Security Notice USN-265-1	     March 23, 2006
libcairo vulnerability
CVE-2006-0528
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 5.10 (Breezy Badger)

The following packages are affected:

libcairo2

The problem can be corrected by upgrading the affected package to
version 1.0.2-0ubuntu1.1. In general, a standard system upgrade is
sufficient to effect the necessary changes.

Details follow:

When rendering glyphs, the cairo graphics rendering library did not
check the maximum length of character strings. A request to display
an excessively long string with cairo caused a program crash due to an
X library error.

Mike Davis discovered that this could be turned into a Denial of
Service attack in Evolution. An email with an attachment with very
long lines caused Evolution to crash repeatedly until that email was
manually removed from the mail folder.

This only affects Ubuntu 5.10. Previous Ubuntu releases did not use
libcairo for text rendering.


  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo_1.0.2-0ubuntu1.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo_1.0.2-0ubuntu1.1.diff.gz)
      Size/MD5:    14177 884cd3ad27785ac78aab5deb8cd31d9a
    [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo_1.0.2-0ubuntu1.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo_1.0.2-0ubuntu1.1.dsc)
      Size/MD5:      748 70fa6ff25b4fffe105a47a51cda5fc33
    [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo_1.0.2.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo_1.0.2.orig.tar.gz)
      Size/MD5:  1458903 d0b7111a14f90ec3afa777ec40c44984

  Architecture independent packages:

    [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2-doc_1.0.2-0ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2-doc_1.0.2-0ubuntu1.1_all.deb)
      Size/MD5:   212994 e7c990a09f1c808dfd748602c276145e

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2-dev_1.0.2-0ubuntu1.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2-dev_1.0.2-0ubuntu1.1_amd64.deb)
      Size/MD5:   339828 b973ef52a7cf03ccb9ce33b3a5f20ce6
    [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.0.2-0ubuntu1.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.0.2-0ubuntu1.1_amd64.deb)
      Size/MD5:   286302 faf2bb5520043b2e42f0fbd4aef74e83

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2-dev_1.0.2-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2-dev_1.0.2-0ubuntu1.1_i386.deb)
      Size/MD5:   312730 fd04bdd0a75954bd77da98d0c5e4a0b3
    [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.0.2-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.0.2-0ubuntu1.1_i386.deb)
      Size/MD5:   269248 efbcf5f0a02cc3a1fbd8d48fd3adeed9

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2-dev_1.0.2-0ubuntu1.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2-dev_1.0.2-0ubuntu1.1_powerpc.deb)
      Size/MD5:   321256 cbaabdb16a7e2ee6dfc099ef388dfd78
    [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.0.2-0ubuntu1.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.0.2-0ubuntu1.1_powerpc.deb)
      Size/MD5:   272914 6a67ee450397d760b607470d5d749bde

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce (AT) lists (DOT) ubuntu.com[/email]
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

iD8DBQFEIqZDDecnbV4Fd/IRAplhAKCsGi71sQtjQqBSh2OTcDqToO585QCeMqG1
e6VTTSDWpFLh7rFP1OvVzoo=
=oCBG
-----END PGP SIGNATURE-----

---

