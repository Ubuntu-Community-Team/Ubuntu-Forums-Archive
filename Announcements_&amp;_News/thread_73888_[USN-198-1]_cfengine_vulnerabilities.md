---
title: "[USN-198-1] cfengine vulnerabilities"
date: 2005-10-10
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-10-10
===========================================================
Ubuntu Security Notice USN-198-1	   October 10, 2005
cfengine vulnerabilities
CAN-2005-2960, CAN-2005-3137
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)
Ubuntu 5.04 (Hoary Hedgehog)

The following packages are affected:

cfengine

The problem can be corrected by upgrading the affected package to
version 1.6.5-1ubuntu0.4.10.1 (for Ubuntu 4.10), or
1.6.5-1ubuntu0.5.04.1 (for Ubuntu 5.04).  In general, a standard
system upgrade is sufficient to effect the necessary changes.

Details follow:

Javier Fernández-Sanguino Peña discovered that several tools in the
cfengine package (vicf, cfmailfilter, and cfcron) create and use
temporary files in an insecure way. A local attacker could exploit
this with a symlink attack to create or overwrite arbitrary files with
the privileges of the user running the cfengine program.


Updated packages for Ubuntu 4.10:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5-1ubuntu0.4.10.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5-1ubuntu0.4.10.1.diff.gz)
      Size/MD5:   102867 ebd2d4596fe81bad3f87b69c0a1057cd
    [http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5-1ubuntu0.4.10.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5-1ubuntu0.4.10.1.dsc)
      Size/MD5:      704 1cde3ab958c48f9cb64eb7005e44bfe9
    [http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5-1ubuntu0.4.10.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5-1ubuntu0.4.10.diff.gz)
      Size/MD5:   102863 0fe4462348ac5db6e48f5ae4200223ee
    [http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5.orig.tar.gz)
      Size/MD5:   880066 fc02d8d56433f32020c3030192cad66e

  Architecture independent packages:

    [http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine-doc_1.6.5-1ubuntu0.4.10.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine-doc_1.6.5-1ubuntu0.4.10.1_all.deb)
      Size/MD5:   351924 ed29a178c45c8c539ef3b04afcefded0

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/universe/c/cfengine/cfengine_1.6.5-1ubuntu0.4.10.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cfengine/cfengine_1.6.5-1ubuntu0.4.10.1_amd64.deb)
      Size/MD5:   353892 44c62122d59a5f0974ad033dc6e80b4a

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/universe/c/cfengine/cfengine_1.6.5-1ubuntu0.4.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cfengine/cfengine_1.6.5-1ubuntu0.4.10.1_i386.deb)
      Size/MD5:   311784 cb66ad235cfdbe07a8f29d9d09f5e073

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/universe/c/cfengine/cfengine_1.6.5-1ubuntu0.4.10.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cfengine/cfengine_1.6.5-1ubuntu0.4.10.1_powerpc.deb)
      Size/MD5:   354564 4bdd42ce5b05c00bc314cb06df597dc3

Updated packages for Ubuntu 5.04:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5-1ubuntu0.5.04.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5-1ubuntu0.5.04.1.diff.gz)
      Size/MD5:   102866 335e8d60109f38507a1f869a58595564
    [http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5-1ubuntu0.5.04.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5-1ubuntu0.5.04.1.dsc)
      Size/MD5:      704 a942df3e7d86a6d1f86126ddb648e6e9
    [http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine_1.6.5.orig.tar.gz)
      Size/MD5:   880066 fc02d8d56433f32020c3030192cad66e

  Architecture independent packages:

    [http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine-doc_1.6.5-1ubuntu0.5.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cfengine/cfengine-doc_1.6.5-1ubuntu0.5.04.1_all.deb)
      Size/MD5:   386022 fcac1e988bae93f33c5da1ea37014055

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/universe/c/cfengine/cfengine_1.6.5-1ubuntu0.5.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cfengine/cfengine_1.6.5-1ubuntu0.5.04.1_amd64.deb)
      Size/MD5:   353878 073ffd567f5b5bfaa3160e878b46d9ba

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/universe/c/cfengine/cfengine_1.6.5-1ubuntu0.5.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cfengine/cfengine_1.6.5-1ubuntu0.5.04.1_i386.deb)
      Size/MD5:   311104 23232672fe6e8eb10f25133cf59680a9

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/universe/c/cfengine/cfengine_1.6.5-1ubuntu0.5.04.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cfengine/cfengine_1.6.5-1ubuntu0.5.04.1_powerpc.deb)
      Size/MD5:   354586 107e028030519395ee526224bdf31da5

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce (AT) lists (DOT) ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.1 (GNU/Linux)

iD8DBQFDSoDqDecnbV4Fd/IRAnwfAJ9/9QP3Jc6wF0/zx3UzwAvB2kNFWQCfXayU
cWiYwOPjsoga/IXhav5qxSQ=
=u3Cz
-----END PGP SIGNATURE-----

---

