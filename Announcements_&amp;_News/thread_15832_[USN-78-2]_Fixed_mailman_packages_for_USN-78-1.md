---
title: "[USN-78-2] Fixed mailman packages for USN-78-1"
date: 2005-02-17
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-02-17
===========================================================
Ubuntu Security Notice USN-78-2		  February 17, 2005
mailman vulnerabilities
CAN-2005-0202
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)

The following packages are affected:

mailman

The problem can be corrected by upgrading the affected package to
version 2.1.5-1ubuntu2.4.  In general, a standard system upgrade is
sufficient to effect the necessary changes.

Details follow:

Ubuntu Security Announce USN-78-1 described a path traversal
vulnerability in the "private" module of Mailman. Unfortunately this
updated mailman package was broken so that the "private" module could
not be executed at all any more. The latest package version fixes
this.

We apologize for the inconvenience.

For reference, this is the description of the original USN:

  An path traversal vulnerability has been discovered in the "private"
  module of Mailman. A flawed path sanitation algorithm allowed the
  construction of URLS to arbitrary files readable by Mailman. This
  allowed a remote attacker to retrieve configuration and password
  databases, private list archives, and other files.


  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.4.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.4.diff.gz)
      Size/MD5:   127333 13d6822a9bbf61a36185f2493197c39b
    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.4.dsc](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.4.dsc)
      Size/MD5:      658 98cd79ac8f48acf3ae3107df66277dfa
    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5.orig.tar.gz)
      Size/MD5:  5745912 f5f56f04747cd4aff67427e7a45631af

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.4_amd64.deb)
      Size/MD5:  6602548 96488545ac4a0f3495d35bb7589884f2

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.4_i386.deb)
      Size/MD5:  6601942 cc724a5e4be27944b8937341257acf48

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.4_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.5-1ubuntu2.4_powerpc.deb)
      Size/MD5:  6610894 e4b91935a6ad14eeba02a116e105be69

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.5 (GNU/Linux)

iD8DBQFCFIBEDecnbV4Fd/IRAhpbAJ9LaVNs22fPgot8s9YSyIW1Bqy2MQCgwK1V
U5s63kmZPLGR9f55NqIXvUA=
=GxAs
-----END PGP SIGNATURE-----

---

