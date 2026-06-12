---
title: "[SOLVED] [USN-119-1] tcpdump vulnerabilities"
date: 2005-05-06
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-05-06
===========================================================
Ubuntu Security Notice USN-119-1	       May 06, 2005
tcpdump vulnerabilities
CAN-2005-1278, CAN-2005-1279, CAN-2005-1280
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)
Ubuntu 5.04 (Hoary Hedgehog)

The following packages are affected:

tcpdump

The problem can be corrected by upgrading the affected package to
version 3.8.3-3ubuntu0.1 (for Ubuntu 4.10), or 3.8.3-3ubuntu0.2 (for
Ubuntu 5.04).  In general, a standard system upgrade is sufficient to
effect the necessary changes.

Details follow:

It was discovered that certain invalid GRE, LDP, BGP, and RSVP packets
triggered infinite loops in tcpdump, which caused tcpdump to stop
working. This could be abused by a remote attacker to bypass tcpdump
analysis of network traffic.

Updated packages for Ubuntu 4.10 (Warty Warthog):

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.1.diff.gz)
      Size/MD5:    10585 6c4901ccc742597d67e32ce32e2f3a5c
    [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.1.dsc)
      Size/MD5:      672 ec71731f2e8f8fcaeb441468b8fd0a8e
    [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3.orig.tar.gz)
      Size/MD5:   567116 30645001f4b97019677cad88d3811904

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.1_amd64.deb)
      Size/MD5:   255638 babb2cd9f5b5fc5d37dc745cb2aeaee6

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.1_i386.deb)
      Size/MD5:   234566 0103496ba2f39329ece8d95dc8f6e4d1

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.1_powerpc.deb)
      Size/MD5:   245482 4bb41525b737a837172f48e99beb5f3d

Updated packages for Ubuntu 5.04 (Hoary Hedgehog):

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.2.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.2.diff.gz)
      Size/MD5:    10623 f1ca38c73c38e02d92a7aa8514e9e0e7
    [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.2.dsc](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.2.dsc)
      Size/MD5:      672 109d4aff0a4e7f770bad49e2af5cd7b0
    [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3.orig.tar.gz)
      Size/MD5:   567116 30645001f4b97019677cad88d3811904

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.2_amd64.deb)
      Size/MD5:   255614 bb885bb99cddaa7d2681e03d3506bd0e

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.2_i386.deb)
      Size/MD5:   234534 88ee0436e9eac9c1fb5b5ffcae2d8e75

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.2_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.2_powerpc.deb)
      Size/MD5:   245540 c5d94ffc34bf3dd1af3725a709b850e5

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.5 (GNU/Linux)

iD8DBQFCex6GDecnbV4Fd/IRAgDsAJ42ahVVfz2Rkjtt0fyj9SswI8k5vwCdF9ei
idR3MbcpIKqy0DOSdlQVnEw=
=1nc4
-----END PGP SIGNATURE-----

---

