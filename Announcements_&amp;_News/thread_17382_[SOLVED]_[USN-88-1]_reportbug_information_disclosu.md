---
title: "[SOLVED] [USN-88-1] reportbug information disclosure"
date: 2005-02-28
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-02-28
===========================================================
Ubuntu Security Notice USN-88-1		  February 28, 2005
reportbug information disclosure
[https://bugzilla.ubuntulinux.org/6600](https://bugzilla.ubuntulinux.org/6600)
[https://bugzilla.ubuntulinux.org/6717](https://bugzilla.ubuntulinux.org/6717)
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)

The following packages are affected:

reportbug

The problem can be corrected by upgrading the affected package to
version 2.62ubuntu1.1.  In general, a standard system upgrade is
sufficient to effect the necessary changes. However, if your users
already have ~/.reportbugrc files with SMTP passwords, you need to
manually change their permissions with

  chmod 600 .reportbugrc

Details follow:

Rolf Leggewie discovered two information disclosure bugs in reportbug.

The per-user configuration file ~/.reportbugrc was created
world-readable. If it contained email smarthost passwords, these were
readable by any other user on the computer storing the home directory.

reportbug usually includes the settings from ~/.reportbugrc in
generated bug reports. This included the "smtppasswd" setting (the
password for an SMTP email smarthost) as well. The password is
now hidden from reports.

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/r/reportbug/reportbug_2.62ubuntu1.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/r/reportbug/reportbug_2.62ubuntu1.1.dsc)
      Size/MD5:      540 19dab43ca7c942311e87ad5e48e32a39
    [http://security.ubuntu.com/ubuntu/pool/main/r/reportbug/reportbug_2.62ubuntu1.1.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/r/reportbug/reportbug_2.62ubuntu1.1.tar.gz)
      Size/MD5:   115256 9b3fbec6a6974274068afb08835f0fdc

  Architecture independent packages:

    [http://security.ubuntu.com/ubuntu/pool/main/r/reportbug/reportbug_2.62ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/r/reportbug/reportbug_2.62ubuntu1.1_all.deb)
      Size/MD5:   104630 f051c98020dffd1e8ae3253ab72e88ce

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.5 (GNU/Linux)

iD8DBQFCIxQUDecnbV4Fd/IRAlnwAJ4j/xMI8mW70dZDcaz6x/B8V2eQ8gCgxhav
qvRVz/h+cPFQHxNgkt26/OY=
=KcxW
-----END PGP SIGNATURE-----

---

