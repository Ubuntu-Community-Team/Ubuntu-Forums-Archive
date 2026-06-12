---
title: "[SOLVED] [USN-369-2] postgresql-8.1 vulnerabilities"
date: 2006-11-01
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2006-11-01
=========================================================== 
Ubuntu Security Notice USN-369-2          November 01, 2006
postgresql-8.1 vulnerabilities
CVE-2006-5540, CVE-2006-5541, CVE-2006-5542
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 6.10

This advisory also applies to the corresponding versions of
Kubuntu, Edubuntu, and Xubuntu.

The problem can be corrected by upgrading your system to the
following package versions:

Ubuntu 6.10:
  postgresql-8.1                           8.1.4-7ubuntu0.1

In general, a standard system upgrade is sufficient to effect the
necessary changes.

Details follow:

USN-369-1 fixed three minor PostgreSQL 8.1 vulnerabilities for Ubuntu 6.06 LTS.
This update provides the corresponding update for Ubuntu 6.10.

Original advisory details:

  Michael Fuhr discovered an incorrect type check when handling unknown
  literals. By attempting to coerce such a literal to the ANYARRAY type,
  a local authenticated attacker could cause a server crash. (CVE-2006-5541)
  
  Josh Drake and Alvaro Herrera reported a crash when using aggregate
  functions in UPDATE statements. A local authenticated attacker could
  exploit this to crash the server backend. This update disables this
  construct, since it is not very well defined and forbidden by the SQL
  standard. (CVE-2006-5540)
  
  Sergey Koposov discovered a flaw in the duration logging. This could
  cause a server crash under certain circumstances. (CVE-2006-5542)
  
  Please note that these flaws can usually not be exploited through web
  and other applications that use a database and are exposed to
  untrusted input, so these flaws do not pose a threat in usual setups.


Updated packages for Ubuntu 6.10:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4-7ubuntu0.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4-7ubuntu0.1.diff.gz)
      Size/MD5:    52401 af21a893e2947a1e467d5e98663031e7
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4-7ubuntu0.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4-7ubuntu0.1.dsc)
      Size/MD5:     1176 04b8d59e5fdb061ebc2a0b1e86c4220d
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4.orig.tar.gz)
      Size/MD5: 11312643 c6554a0ef948ab2b18b617954e1788fe

  Architecture independent packages:

    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-doc-8.1_8.1.4-7ubuntu0.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-doc-8.1_8.1.4-7ubuntu0.1_all.deb)
      Size/MD5:  1442056 4263930dd4391fd81944a82c372f3cba

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-compat2_8.1.4-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-compat2_8.1.4-7ubuntu0.1_amd64.deb)
      Size/MD5:   152924 5fb69c85456514e2f78072efc3956ec0
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-dev_8.1.4-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-dev_8.1.4-7ubuntu0.1_amd64.deb)
      Size/MD5:   344912 a34d581ae43ce95f0758f3128d2c07e5
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg5_8.1.4-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg5_8.1.4-7ubuntu0.1_amd64.deb)
      Size/MD5:   173428 733938955a0112fb6fedc835f5456052
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpgtypes2_8.1.4-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpgtypes2_8.1.4-7ubuntu0.1_amd64.deb)
      Size/MD5:   175450 5412a17f17d49c3090cb7fcbcc136e7b
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq-dev_8.1.4-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq-dev_8.1.4-7ubuntu0.1_amd64.deb)
      Size/MD5:   312606 3b5e8a5d6cffa8b48f82575458503d22
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq4_8.1.4-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq4_8.1.4-7ubuntu0.1_amd64.deb)
      Size/MD5:   206680 559c766535f53918647783563d797582
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4-7ubuntu0.1_amd64.deb)
      Size/MD5:  3256168 a0bbda514074cd42271529eb07e94ecd
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-client-8.1_8.1.4-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-client-8.1_8.1.4-7ubuntu0.1_amd64.deb)
      Size/MD5:   769328 3323f21f5fd11c660e74e0b2a3d480f6
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-contrib-8.1_8.1.4-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-contrib-8.1_8.1.4-7ubuntu0.1_amd64.deb)
      Size/MD5:   619156 08c3d6be3fa11d19eccdbb9986e659d4
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plperl-8.1_8.1.4-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plperl-8.1_8.1.4-7ubuntu0.1_amd64.deb)
      Size/MD5:   169362 d5cec1f551207e2e734bf6fab2317ef9
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plpython-8.1_8.1.4-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plpython-8.1_8.1.4-7ubuntu0.1_amd64.deb)
      Size/MD5:   163748 b99d7a9fafcfd3e8b616ef1f483c4da9
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-pltcl-8.1_8.1.4-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-pltcl-8.1_8.1.4-7ubuntu0.1_amd64.deb)
      Size/MD5:   164056 17bb99f0f7ab3edf2391271d64e0feda
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-server-dev-8.1_8.1.4-7ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-server-dev-8.1_8.1.4-7ubuntu0.1_amd64.deb)
      Size/MD5:   596412 1d3f23de9e73e3f3c97b2532d7b4c5c8

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-compat2_8.1.4-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-compat2_8.1.4-7ubuntu0.1_i386.deb)
      Size/MD5:   152234 5ec67e24a0c39547dd1a4594f43c9ba2
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-dev_8.1.4-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-dev_8.1.4-7ubuntu0.1_i386.deb)
      Size/MD5:   342026 a3628ec749e0d789575496d8ef383a31
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg5_8.1.4-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg5_8.1.4-7ubuntu0.1_i386.deb)
      Size/MD5:   172122 21c2f681f5c623d65d8a8a83ca5ee4fe
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpgtypes2_8.1.4-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpgtypes2_8.1.4-7ubuntu0.1_i386.deb)
      Size/MD5:   175124 547e40b4cdb2fb8f6c01a443b21a9edb
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq-dev_8.1.4-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq-dev_8.1.4-7ubuntu0.1_i386.deb)
      Size/MD5:   305840 49c8db9e9ee18d99ce45c1b4cc64c3b6
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq4_8.1.4-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq4_8.1.4-7ubuntu0.1_i386.deb)
      Size/MD5:   202648 e02cd0e97ea04f3ed9808562cdd61b16
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4-7ubuntu0.1_i386.deb)
      Size/MD5:  3155738 8b8a255cfc36bb6207d4972d30114c4f
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-client-8.1_8.1.4-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-client-8.1_8.1.4-7ubuntu0.1_i386.deb)
      Size/MD5:   739926 42db79545ef912384d45a9e321aa7889
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-contrib-8.1_8.1.4-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-contrib-8.1_8.1.4-7ubuntu0.1_i386.deb)
      Size/MD5:   587552 7b3612cd963fd40b7626f19940f5cc85
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plperl-8.1_8.1.4-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plperl-8.1_8.1.4-7ubuntu0.1_i386.deb)
      Size/MD5:   168202 da95c00f91be43d6c4651144fd5d78ce
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plpython-8.1_8.1.4-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plpython-8.1_8.1.4-7ubuntu0.1_i386.deb)
      Size/MD5:   161630 f781234805909d6efabcd1e0ec42bfc5
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-pltcl-8.1_8.1.4-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-pltcl-8.1_8.1.4-7ubuntu0.1_i386.deb)
      Size/MD5:   163002 76e987350cb8feb799663e0b72c77a4f
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-server-dev-8.1_8.1.4-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-server-dev-8.1_8.1.4-7ubuntu0.1_i386.deb)
      Size/MD5:   596394 460bfba660947b82c1616353d5171e96

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-compat2_8.1.4-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-compat2_8.1.4-7ubuntu0.1_powerpc.deb)
      Size/MD5:   153756 f269e9370aa649d122994aa7907104b5
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-dev_8.1.4-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-dev_8.1.4-7ubuntu0.1_powerpc.deb)
      Size/MD5:   339348 af5a24b146f61084c6b94b796d3a653a
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg5_8.1.4-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg5_8.1.4-7ubuntu0.1_powerpc.deb)
      Size/MD5:   174288 5142ebdd438cf151e0f405ff4855f2dc
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpgtypes2_8.1.4-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpgtypes2_8.1.4-7ubuntu0.1_powerpc.deb)
      Size/MD5:   178260 0d0a813c48e899bb9cff5a41a8398fbd
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq-dev_8.1.4-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq-dev_8.1.4-7ubuntu0.1_powerpc.deb)
      Size/MD5:   308032 c11439a9a23ead70ddb60fd1b2264003
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq4_8.1.4-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq4_8.1.4-7ubuntu0.1_powerpc.deb)
      Size/MD5:   204732 019d45db40122878bd2f64e25b58702f
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4-7ubuntu0.1_powerpc.deb)
      Size/MD5:  3555700 d07b565f5be335ff6761da96b7d88f26
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-client-8.1_8.1.4-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-client-8.1_8.1.4-7ubuntu0.1_powerpc.deb)
      Size/MD5:   779658 251e7a8eed17c33eb868dcf0018970d7
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-contrib-8.1_8.1.4-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-contrib-8.1_8.1.4-7ubuntu0.1_powerpc.deb)
      Size/MD5:   639686 bea4a0e9f449f75f56554c79f252e9fd
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plperl-8.1_8.1.4-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plperl-8.1_8.1.4-7ubuntu0.1_powerpc.deb)
      Size/MD5:   169106 16226facd3e893b889cb72eb9e8df42c
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plpython-8.1_8.1.4-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plpython-8.1_8.1.4-7ubuntu0.1_powerpc.deb)
      Size/MD5:   163948 d9996a974e94652834ca4c1d1df5013d
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-pltcl-8.1_8.1.4-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-pltcl-8.1_8.1.4-7ubuntu0.1_powerpc.deb)
      Size/MD5:   165024 2df3b4f4878f006eec5ce7305672d752
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-server-dev-8.1_8.1.4-7ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-server-dev-8.1_8.1.4-7ubuntu0.1_powerpc.deb)
      Size/MD5:   596432 d35808efc5c022dab90461e0dccfccca

  sparc architecture (Sun SPARC/UltraSPARC)

    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-compat2_8.1.4-7ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-compat2_8.1.4-7ubuntu0.1_sparc.deb)
      Size/MD5:   151610 d7e6bb8c226664538a41c05bd8efcc80
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-dev_8.1.4-7ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg-dev_8.1.4-7ubuntu0.1_sparc.deb)
      Size/MD5:   335088 b0309c99b0f904414afaf29e27ef4aa0
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg5_8.1.4-7ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libecpg5_8.1.4-7ubuntu0.1_sparc.deb)
      Size/MD5:   171724 474c5c7903229f404bc042d00910fe34
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpgtypes2_8.1.4-7ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpgtypes2_8.1.4-7ubuntu0.1_sparc.deb)
      Size/MD5:   173454 dcd4fc4f2550bf80130fb7e1b02da2b4
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq-dev_8.1.4-7ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq-dev_8.1.4-7ubuntu0.1_sparc.deb)
      Size/MD5:   305174 268c509165f58d3ef83491e49cfbdda2
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq4_8.1.4-7ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq4_8.1.4-7ubuntu0.1_sparc.deb)
      Size/MD5:   201412 d5e3d6dcca7b83ba18a90da314443c26
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4-7ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-8.1_8.1.4-7ubuntu0.1_sparc.deb)
      Size/MD5:  3482382 515aaee1feeda7549efb2543cf30b167
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-client-8.1_8.1.4-7ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-client-8.1_8.1.4-7ubuntu0.1_sparc.deb)
      Size/MD5:   754506 cc62cd3ba7ecb37f88a0a13abb0c7a49
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-contrib-8.1_8.1.4-7ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-contrib-8.1_8.1.4-7ubuntu0.1_sparc.deb)
      Size/MD5:   598348 fb2b4f26146e27d75c2ed580f2b59be0
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plperl-8.1_8.1.4-7ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plperl-8.1_8.1.4-7ubuntu0.1_sparc.deb)
      Size/MD5:   167762 69bfb050570fc151fb2d251855ded8f4
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plpython-8.1_8.1.4-7ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-plpython-8.1_8.1.4-7ubuntu0.1_sparc.deb)
      Size/MD5:   162366 4a38b861e8eb528bc4e96e1f64b27a04
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-pltcl-8.1_8.1.4-7ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-pltcl-8.1_8.1.4-7ubuntu0.1_sparc.deb)
      Size/MD5:   163042 68c9e99678283f3b2cf0f73db8b845e2
    [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-server-dev-8.1_8.1.4-7ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/postgresql-server-dev-8.1_8.1.4-7ubuntu0.1_sparc.deb)
      Size/MD5:   596424 5a9b3e7626e3664578060f8292199f62

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce (AT) lists (DOT) ubuntu.com[/email]
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.3 (GNU/Linux)

iD8DBQFFSIO8DecnbV4Fd/IRAoH+AKCBNqOq+z2LuYJ7pr0HzSa9fRIz1QCeNDyI
Xe8lFPu+6cLcoUtnTVFEQ3Q=
=3G8y
-----END PGP SIGNATURE-----

---

