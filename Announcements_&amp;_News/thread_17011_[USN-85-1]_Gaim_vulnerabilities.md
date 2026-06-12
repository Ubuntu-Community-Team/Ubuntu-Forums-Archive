---
title: "[USN-85-1] Gaim vulnerabilities"
date: 2005-02-25
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-02-25
===========================================================
Ubuntu Security Notice USN-85-1		  February 25, 2005
gaim vulnerabilities
CAN-2005-0208, CAN-2005-0472, CAN-2005-0473
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)

The following packages are affected:

gaim

The problem can be corrected by upgrading the affected package to
version 1:1.0.0-1ubuntu1.2.  In general, a standard system upgrade is
sufficient to effect the necessary changes.

Details follow:

The Gaim developers discovered that the HTML parser did not
sufficiently validate its input. This allowed a remote attacker to
crash the Gaim client by sending certain malformed HTML messages.
(CAN-2005-0208, CAN-2005-0473)

Another lack of sufficient input validation was found in the "Oscar"
protocol handler which is used for ICQ and AIM. By sending specially
crafted packets, remote users could trigger an infinite loop in Gaim
which caused Gaim to become unresponsive and hang. (CAN-2005-0472)

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.2.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.2.diff.gz)
      Size/MD5:    42432 088aa80f79950d5efa7f6afc29d2915e
    [http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.2.dsc](http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.2.dsc)
      Size/MD5:      853 66848ad2c5b6ef2c136e8419d9c84e72
    [http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0.orig.tar.gz)
      Size/MD5:  6985979 7dde686aace751a49dce734fd0cb7ace

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.2_amd64.deb)
      Size/MD5:  3444018 f829005df6031fa36622e04bcb30968e

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.2_i386.deb)
      Size/MD5:  3354146 f85b4b98fc5bc04fe494a5303f225967

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.2_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.2_powerpc.deb)
      Size/MD5:  3417968 614a7816b433efb292944822479661b1

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.5 (GNU/Linux)

iD8DBQFCH0usDecnbV4Fd/IRAiqhAKCVlT1f5aQ5vBEHPMOTUovzqGswLACg8QjC
FOOj2N8fUbJJVp3iiu4ShD0=
=yWRH
-----END PGP SIGNATURE-----

---

