---
title: "[SOLVED] [USN-12-1] ppp Denial of Service"
date: 2004-10-29
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2004-10-29
===========================================================
Ubuntu Security Notice USN-12-1            October 29, 2004
ppp Denial of Service
[http://www.securityfocus.com/archive/1/379450](http://www.securityfocus.com/archive/1/379450)
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)

The following packages are affected:

ppp

The problem can be corrected by upgrading the affected packages to
version 2.4.2+20040428-2ubuntu6.2. In general, a standard system
upgrade is sufficient to effect the necessary changes.

Details follow:

It has been discovered that ppp does not properly verify certain data
structures used in the CBCP protocol. This vulnerability could allow
an attacker to cause the pppd server to crash due to an invalid memory
access, leading to a denial of service. However, there is no
possibility of code execution or privilege escalation.

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp_2.4.2+20040428-2ubuntu6.2.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp_2.4.2+20040428-2ubuntu6.2.diff.gz)
      Size/MD5:    71343 2cc5486014e37d195fd54b3f2dbd8a31
    [http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp_2.4.2+20040428-2ubuntu6.2.dsc](http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp_2.4.2+20040428-2ubuntu6.2.dsc)
      Size/MD5:      661 24d306be11f2ef98b879cb97ffaf6c06
    [http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp_2.4.2+20040428.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp_2.4.2+20040428.orig.tar.gz)
      Size/MD5:   801353 cc76377ffca35e745838ab82ea4474cd

  Architecture independent packages:

    [http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp-dev_2.4.2+20040428-2ubuntu6.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp-dev_2.4.2+20040428-2ubuntu6.2_all.deb)
      Size/MD5:    31824 7d044f9782cded224269c53253e0b0bd

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp-udeb_2.4.2+20040428-2ubuntu6.2_amd64.udeb](http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp-udeb_2.4.2+20040428-2ubuntu6.2_amd64.udeb)
      Size/MD5:   111708 e904c4e2318df41bbd55cb7214e249f6
    [http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp_2.4.2+20040428-2ubuntu6.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp_2.4.2+20040428-2ubuntu6.2_amd64.deb)
      Size/MD5:   309720 776feee80231a3b7f2afaa855dabbf58

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp-udeb_2.4.2+20040428-2ubuntu6.2_i386.udeb](http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp-udeb_2.4.2+20040428-2ubuntu6.2_i386.udeb)
      Size/MD5:    94838 d3b9d5580e427b876040a07b507d04fc
    [http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp_2.4.2+20040428-2ubuntu6.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp_2.4.2+20040428-2ubuntu6.2_i386.deb)
      Size/MD5:   285512 1a431f211803cf2ae12c5923b72dfbda

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp-udeb_2.4.2+20040428-2ubuntu6.2_powerpc.udeb](http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp-udeb_2.4.2+20040428-2ubuntu6.2_powerpc.udeb)
      Size/MD5:   107248 624f06af49245eecd5f93275497cc58b
    [http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp_2.4.2+20040428-2ubuntu6.2_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/ppp/ppp_2.4.2+20040428-2ubuntu6.2_powerpc.deb)
      Size/MD5:   308390 df4f46685a94c5c01cf6f4ba1e02704b

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.4 (GNU/Linux)

iD8DBQFBggu8DecnbV4Fd/IRAvMaAKCNAhXpJ+u23e/yMgHhs6xVqv67QQCfZ9Iy
mDoegyg7KNaDv4eIOHiWKn8=
=JVzE
-----END PGP SIGNATURE-----

---

