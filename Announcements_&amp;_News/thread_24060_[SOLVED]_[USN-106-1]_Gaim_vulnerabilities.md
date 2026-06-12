---
title: "[SOLVED] [USN-106-1] Gaim vulnerabilities"
date: 2005-04-05
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-04-05
===========================================================
Ubuntu Security Notice USN-106-1	     April 05, 2005
gaim vulnerabilities
CAN-2005-0965, CAN-2005-0966
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)

The following packages are affected:

gaim

The problem can be corrected by upgrading the affected package to
version 1:1.0.0-1ubuntu1.3. You have to restart gaim after a standard
system upgrade to effect the necessary changes. 

Details follow:

Jean-Yves Lefort discovered a buffer overflow in the
gaim_markup_strip_html() function. This caused Gaim to crash when
receiving certain malformed HTML messages. (CAN-2005-0965)

Jean-Yves Lefort also noticed that many functions that handle IRC
commands do not escape received HTML metacharacters; this allowed
remote attackers to cause a Denial of Service by injecting arbitrary
HTML code into the conversation window, popping up arbitrarily many
empty dialog boxes, or even causing Gaim to crash. (CAN-2005-0966)

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.3.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.3.diff.gz)
      Size/MD5:    44905 d03a90434a68d12eb361fd9fbfca7d91
    [http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.3.dsc](http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.3.dsc)
      Size/MD5:      853 7da3670bdef956122725699e38775026
    [http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0.orig.tar.gz)
      Size/MD5:  6985979 7dde686aace751a49dce734fd0cb7ace

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.3_amd64.deb)
      Size/MD5:  3444332 f844c3edb768a56d5404589b9c42651b

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.3_i386.deb)
      Size/MD5:  3354832 61ef71028ec730ee598d889a75588189

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.3_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.0-1ubuntu1.3_powerpc.deb)
      Size/MD5:  3418174 e0d906d95a46f99de375efabbe713781

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.5 (GNU/Linux)

iD8DBQFCUo2FDecnbV4Fd/IRArByAJ9udjjnRss9KhiAyGO7f04ySw7tdwCg0mt2
2l3QusD/iAlKewT8iIzpxhs=
=G5Iz
-----END PGP SIGNATURE-----

---

