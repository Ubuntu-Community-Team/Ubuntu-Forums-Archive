---
title: "[SOLVED] [USN-3-1] GhostScript utility script vulnerabilities"
date: 2004-10-26
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2004-10-26
===========================================================
Ubuntu Security Notice USN-3-1             October 27, 2004
GhostScript utility script vulnerabilities
CAN-2004-0967
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)

The following packages are affected:

gs-common

The problem can be corrected by upgrading the affected package to
version 0.3.6ubuntu1.1. In general, a standard system upgrade is
sufficient to effect the necessary changes.

Details follow:

Recently, Trustix Secure Linux discovered some vulnerabilities in the
gs-common package. The utilities "pv.sh" and "ps2epsi" created
temporary files in an insecure way, which allowed a symlink attack to
create or overwrite arbitrary files with the privileges of the user
invoking the program.

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/g/gs-common/gs-common_0.3.6ubuntu1.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/g/gs-common/gs-common_0.3.6ubuntu1.1.dsc)
      Size/MD5:      589 3506426ff7ecd78fea5e254dbf694b35
    [http://security.ubuntu.com/ubuntu/pool/main/g/gs-common/gs-common_0.3.6ubuntu1.1.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/g/gs-common/gs-common_0.3.6ubuntu1.1.tar.gz)
      Size/MD5:    31596 060a50ce728aedeb61d6b17be30d2e5d

  Architecture independent packages:

    [http://security.ubuntu.com/ubuntu/pool/main/g/gs-common/gs-common_0.3.6ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gs-common/gs-common_0.3.6ubuntu1.1_all.deb)
      Size/MD5:    45434 8ca2afdfe91cd67777f44f767489a705

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.4 (GNU/Linux)

iD8DBQFBfu7dDecnbV4Fd/IRAn13AKC8Y+5sLv7WnZLnBQXTi9n4tvdk1gCfXwW8
GIq1xF0hK6UcCrd0usdTUwY=
=5w7E
-----END PGP SIGNATURE-----

---

