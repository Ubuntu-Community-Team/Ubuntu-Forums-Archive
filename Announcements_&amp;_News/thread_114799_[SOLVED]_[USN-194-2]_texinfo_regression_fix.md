---
title: "[SOLVED] [USN-194-2] texinfo regression fix"
date: 2006-01-09
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2006-01-09
===========================================================
Ubuntu Security Notice USN-194-2	   January 09, 2006
texinfo regression bug fix
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 5.04 (Hoary Hedgehog)
Ubuntu 5.10 (Breezy Badger)

The following packages are affected:

texinfo

The problem can be corrected by upgrading the affected package to
version 4.7-2.2ubuntu1.2 (for Ubuntu 5.04) or 4.7-2.2ubuntu2.1 (for
Ubuntu 5.10).  In general, a standard system upgrade is sufficient to
effect the necessary changes.

Details follow:

USN-194-1 fixed a vulnerability in the 'texindex' program.
Unfortunately this update introduced a regression that caused the
program to abort when cleaning up temporary files (which are used with
extraordinarily large input files). The updated packages fix this.

Updated packages for Ubuntu 5.04:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu1.2.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu1.2.diff.gz)
      Size/MD5:    11620 388c10268994c27d5de4ad61ca43af10
    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu1.2.dsc](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu1.2.dsc)
      Size/MD5:      628 b1187a4c357c1bbde7ca7d3a0f7ef3fe
    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7.orig.tar.gz)
      Size/MD5:  1979183 72a57e378efb9898c9e41ca839554dae

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu1.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu1.2_amd64.deb)
      Size/MD5:   191400 363d593823cf147269189e46959cbe15
    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu1.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu1.2_amd64.deb)
      Size/MD5:   488300 5d5e124c2cc75e99c6028a866e731552

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu1.2_i386.deb)
      Size/MD5:   177636 7e3b1b3a738d673df06f77bb0f6d336b
    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu1.2_i386.deb)
      Size/MD5:   470644 f9ad98c26ab20b2fe997874780ae8c10

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu1.2_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu1.2_powerpc.deb)
      Size/MD5:   190454 21ae8ae5a8b1c159e2a19ee2d213d5a2
    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu1.2_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu1.2_powerpc.deb)
      Size/MD5:   484020 9e84710926bb7fc154de15ed0b284c83

Updated packages for Ubuntu 5.10:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu2.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu2.1.diff.gz)
      Size/MD5:    11627 753a4bd4f338d4c4fc78c379520bd6d8
    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu2.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu2.1.dsc)
      Size/MD5:      628 f4fecdec0d663ea1b9478426cd46f3e3
    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7.orig.tar.gz)
      Size/MD5:  1979183 72a57e378efb9898c9e41ca839554dae

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu2.1_amd64.deb)
      Size/MD5:   192564 c8ff9c2f511f1fa252a9b03b061bbef5
    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu2.1_amd64.deb)
      Size/MD5:   493770 c8b002f2f4d7c41175072eec89f3133a

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu2.1_i386.deb)
      Size/MD5:   177584 1a9cdc5f2bbefe6d7813aac523ebf83b
    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu2.1_i386.deb)
      Size/MD5:   473226 aa19cbabe722ebc543b501ec7f62bce1

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu2.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu2.1_powerpc.deb)
      Size/MD5:   191098 edacc9d3b5423b2bc1ae3986f420be8d
    [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu2.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.7-2.2ubuntu2.1_powerpc.deb)
      size/md5:   485862 c04dc10507d4efe22f212664ccfb593c

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce (AT) lists (DOT) ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.2 (GNU/Linux)

iD8DBQFDwnW+DecnbV4Fd/IRAhJKAKDbHRFAbUVf30xgzMB5HZYdSkX5AgCfXIyU
5PdlyfBPRkHknMwCmJlb2FI=
=fcwr
-----END PGP SIGNATURE-----

---

