---
title: "[USN-84-1] Squid vulnerabilities"
date: 2005-02-21
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-02-21
===========================================================
Ubuntu Security Notice USN-84-1		  February 21, 2005
squid vulnerabilities
CAN-2005-0194, CAN-2005-0446
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)

The following packages are affected:

squid

The problem can be corrected by upgrading the affected package to
version 2.5.5-6ubuntu0.5.  In general, a standard system upgrade is
sufficient to effect the necessary changes.

Details follow:

When parsing the configuration file, squid interpreted empty Access
Control Lists (ACLs) without defined authentication schemes in a
non-obvious way. This could allow remote attackers to bypass intended
ACLs. (CAN-2005-0194)

A remote Denial of Service vulnerability was discovered in the domain
name resolution code. A faulty or malicious DNS server could stop the
Squid server immediately by sending a malformed IP address.
(CAN-2005-0446)

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.5.5-6ubuntu0.5.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.5.5-6ubuntu0.5.diff.gz)
      Size/MD5:   273103 b227505fff84a15f636d1a40ef894a59
    [http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.5.5-6ubuntu0.5.dsc](http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.5.5-6ubuntu0.5.dsc)
      Size/MD5:      652 03dda2b1794bee143c7bb2c907177dec
    [http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.5.5.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.5.5.orig.tar.gz)
      Size/MD5:  1363967 6c7f3175b5fa04ab5ee68ce752e7b500

  Architecture independent packages:

    [http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid-common_2.5.5-6ubuntu0.5_all.deb](http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid-common_2.5.5-6ubuntu0.5_all.deb)
      Size/MD5:   190542 18ac376117476528d04ecf34c39605c5

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/universe/s/squid/squid-cgi_2.5.5-6ubuntu0.5_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/s/squid/squid-cgi_2.5.5-6ubuntu0.5_amd64.deb)
      Size/MD5:    89972 6c0d1ca2955e65c617a0ffb9835fb7d0
    [http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.5.5-6ubuntu0.5_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.5.5-6ubuntu0.5_amd64.deb)
      Size/MD5:   812832 c4ae1fa8c10241c975be5a5ae713d259
    [http://security.ubuntu.com/ubuntu/pool/universe/s/squid/squidclient_2.5.5-6ubuntu0.5_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/s/squid/squidclient_2.5.5-6ubuntu0.5_amd64.deb)
      Size/MD5:    71320 6426cdd50abe26ff32430f10384f98b6

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/universe/s/squid/squid-cgi_2.5.5-6ubuntu0.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/s/squid/squid-cgi_2.5.5-6ubuntu0.5_i386.deb)
      Size/MD5:    88484 048eee3bff6f8c1c2a27c422d8d02878
    [http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.5.5-6ubuntu0.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.5.5-6ubuntu0.5_i386.deb)
      Size/MD5:   728800 86015fa3f0e70ca114d50600779a5218
    [http://security.ubuntu.com/ubuntu/pool/universe/s/squid/squidclient_2.5.5-6ubuntu0.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/s/squid/squidclient_2.5.5-6ubuntu0.5_i386.deb)
      Size/MD5:    70052 fa490312c320b567d0a2ab9aa86516a9

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/universe/s/squid/squid-cgi_2.5.5-6ubuntu0.5_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/universe/s/squid/squid-cgi_2.5.5-6ubuntu0.5_powerpc.deb)
      Size/MD5:    89398 69752585a510d3e5fd35f3855d316354
    [http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.5.5-6ubuntu0.5_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.5.5-6ubuntu0.5_powerpc.deb)
      Size/MD5:   796142 ce07df2197a74e4da2325e39e153b38a
    [http://security.ubuntu.com/ubuntu/pool/universe/s/squid/squidclient_2.5.5-6ubuntu0.5_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/universe/s/squid/squidclient_2.5.5-6ubuntu0.5_powerpc.deb)
      Size/MD5:    70814 1074527b3d8dc744aa1b128713c902ba

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.5 (GNU/Linux)

iD8DBQFCGfJWDecnbV4Fd/IRAqmnAKCkgIDBmkFRUV8+Ey+xg4yicZnqFwCeOD21
y/oC8BlvnEMjmsg+bF+C6Bg=
=djNW
-----END PGP SIGNATURE-----

---

