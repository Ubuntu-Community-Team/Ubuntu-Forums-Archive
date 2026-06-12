---
title: "[SOLVED] [USN-116-1] gzip vulnerabilities"
date: 2005-05-04
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-05-04
===========================================================
Ubuntu Security Notice USN-116-1	       May 04, 2005
gzip vulnerabilities
CAN-2005-0988, CAN-2005-1228
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)
Ubuntu 5.04 (Hoary Hedgehog)

The following packages are affected:

gzip

The problem can be corrected by upgrading the affected package to
version 1.3.5-9ubuntu3.1 (for Ubuntu 4.10), or 1.3.5-9ubuntu3.2 (for
Ubuntu 5.04).  In general, a standard system upgrade is sufficient to
effect the necessary changes.

Details follow:

Imran Ghory discovered a race condition in the file permission restore
code of gzip and gunzip. While a user was compressing or decompressing
a file, a local attacker with write permissions in the directory of
that file could replace the target file with a hard link.  This would
cause gzip to restore the file permissions to the hard link target
instead of to the gzip output file, which could be exploited to gain
read or even write access to files of other users.  (CAN-2005-0988)

Ulf Harnhammar found a path traversal vulnerability when gunzip was
used with the -N option. An attacker could exploit this to create
files in an arbitrary directory with the permissions of a user if he
tricked this user to decompress a specially crafted gzip file using
the -N option (which can also happen in systems that automatically
process uploaded gzip files). (CAN-2005-1228)

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.1.diff.gz)
      Size/MD5:    58960 9c331f78bcee51c334fb6dd2fcea3878
    [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.1.dsc)
      Size/MD5:      570 e497a2855c0b13d815bcb4153f687a67
    [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5.orig.tar.gz)
      Size/MD5:   331550 3d6c191dfd2bf307014b421c12dc8469

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.1_amd64.deb)
      Size/MD5:    75364 88ae760a3a95bbc077aca0ffc45a3a25

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.1_i386.deb)
      Size/MD5:    70262 2d29d42efac460692dbfded6d3adfee5

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.1_powerpc.deb)
      Size/MD5:    76884 f917e7fe2e2cf330123a97e47f891541

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.2.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.2.diff.gz)
      Size/MD5:    58990 2f72cdc16ee3e211cc36d9876f68ec43
    [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.2.dsc](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.2.dsc)
      Size/MD5:      570 5110df80ff53f90168a67475356d771d
    [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5.orig.tar.gz)
      Size/MD5:   331550 3d6c191dfd2bf307014b421c12dc8469

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.2_amd64.deb)
      Size/MD5:    75480 426bee20a69bb255692cb7be99ca4d0b

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.2_i386.deb)
      Size/MD5:    70288 dfed746ac6a4513ddd35dabfd4552d85

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.2_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.2_powerpc.deb)
      Size/MD5:    77028 1d10416664379d87e22ca6305628b328

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.5 (GNU/Linux)

iD8DBQFCeJNKDecnbV4Fd/IRAgsvAKDn31hvqi2b0kBcWtj3Db64MqL/vwCg1lz/
gsQ913rrDcm88MC5/FELCKc=
=Fyjj
-----END PGP SIGNATURE-----

---

