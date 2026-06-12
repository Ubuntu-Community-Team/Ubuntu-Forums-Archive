---
title: "[SOLVED] [USN-242-1] mailman vulnerabilities"
date: 2006-01-16
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2006-01-16
===========================================================
Ubuntu Security Notice USN-242-1	   January 16, 2006
mailman vulnerabilities
CVE-2005-3573, CVE-2005-4153
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)
Ubuntu 5.04 (Hoary Hedgehog)
Ubuntu 5.10 (Breezy Badger)

The following packages are affected:

mailman

The problem can be corrected by upgrading the affected package to
version 2.1.5-1ubuntu2.5 (for Ubuntu 4.10), 2.1.5-7ubuntu0.1 (for
Ubuntu 5.04), or 2.1.5-8ubuntu2.1 (for Ubuntu 5.10).  In general, a
standard system upgrade is sufficient to effect the necessary changes.

Details follow:

Aliet Santiesteban Sifontes discovered a remote Denial of Service
vulnerability in the attachment handler. An email with an attachment
whose filename contained invalid UTF-8 characters caused mailman to
crash. (CVE-2005-3573)

Mailman did not sufficiently verify the validity of email dates. Very
large numbers in dates caused mailman to crash. (CVE-2005-4153)


Updated packages for Ubuntu 4.10:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.5.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.5.diff.gz)
      Size/MD5:   128899 1686924bbacf9fefa556fd7f1e8f74dc
    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.5.dsc](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.5.dsc)
      Size/MD5:      658 65e41dc9eb2456d8189aea0eb4df64ae
    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5.orig.tar.gz)
      Size/MD5:  5745912 f5f56f04747cd4aff67427e7a45631af

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.5_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.5_amd64.deb)
      Size/MD5:  6602720 b559d0c6c0c8d97dc6ea342a4911d154

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.5_i386.deb)
      Size/MD5:  6602194 ad5e65cead5a9d90ddbffc736337fb94

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.5_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.5_powerpc.deb)
      Size/MD5:  6611016 89feb8e459fa9f34ff91c8bbf75f3a80

Updated packages for Ubuntu 5.04:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-7ubuntu0.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-7ubuntu0.1.diff.gz)
      Size/MD5:   118355 78b91e2f11e438ef259c3e67e6fd1d47
    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-7ubuntu0.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-7ubuntu0.1.dsc)
      Size/MD5:      669 99b42b16f8c4ba4e8acacc73920d1639
    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5.orig.tar.gz)
      Size/MD5:  5745912 f5f56f04747cd4aff67427e7a45631af

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-7ubuntu0.1_amd64.deb)
      Size/MD5:  6609778 28b3e1f005cbcc097fb084ba3b0c313b

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-7ubuntu0.1_i386.deb)
      Size/MD5:  6609308 f80df6c6bc8f6a028d065c8892849569

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-7ubuntu0.1_powerpc.deb)
      Size/MD5:  6616534 f33e0b4a6d2afea8aa96f3e86fdfe579

Updated packages for Ubuntu 5.10:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-8ubuntu2.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-8ubuntu2.1.diff.gz)
      Size/MD5:   194039 fd67dfe7d97bd94e9ad0e0575599639d
    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-8ubuntu2.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-8ubuntu2.1.dsc)
      Size/MD5:      626 63366d888d62e4769c331c7303716c2e
    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5.orig.tar.gz)
      Size/MD5:  5745912 f5f56f04747cd4aff67427e7a45631af

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-8ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-8ubuntu2.1_amd64.deb)
      Size/MD5:  6610440 165e35634f6767fbab615e9407eec4c8

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-8ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-8ubuntu2.1_i386.deb)
      Size/MD5:  6609374 03e1822d1085b4ff27d3ecb2912048bf

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-8ubuntu2.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-8ubuntu2.1_powerpc.deb)
      Size/MD5:  6617106 522653cd7ecdce70366a2d80b5b97460

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce (AT) lists (DOT) ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.2 (GNU/Linux)

iD8DBQFDy3lODecnbV4Fd/IRAuEUAJ0VuY2/gZWqMRJqN+NCeilBG/fYAgCgsTTi
9gNmu3WXo7onwC9cozI2pgM=
=KxVk
-----END PGP SIGNATURE-----

---

