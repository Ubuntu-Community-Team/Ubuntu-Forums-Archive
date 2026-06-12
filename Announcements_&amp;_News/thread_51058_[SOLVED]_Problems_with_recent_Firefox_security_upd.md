---
title: "[SOLVED] Problems with recent Firefox security update"
date: 2005-07-22
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-07-22
Dear Hoary users,

yesterday a security update for Mozilla Firefox was relased
(USN-149-1). Many users seem to have problems with the new version, it
crashes very often.

The problem is that one of the security patches changed the API (the
interface that extensions use to integrate with the browser), which
breaks many extensions. Similar problems happen with the upstream
release 1.0.6, so using that does not help very much.

To get an usable browser quickly, you have two options:

1) Uninstall extensions. Some extensions (like mozilla-tabextension,
   which is also packaged in Ubuntu universe) that rely on the old
   interface cause the browser to crash. Other extensions (like AdBlock)
   run fine.

or

2) Downgrade to the Hoary version:

   sudo apt-get install mozilla-firefox=1.0.2-0ubuntu5 mozilla-firefox-gnome-support=1.0.2-0ubuntu5

   However, this will expose you to a lot of vulnerabilities.

This issue is also tracked in Bugzilla:

  [https://bugzilla.ubuntu.com/show_bug.cgi?id=12854](https://bugzilla.ubuntu.com/show_bug.cgi?id=12854)

We will continue to track this issue and try to find a long term solution.

We apologize for the inconvenience,

Martin Pitt
Ubuntu Security Team leader

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.1 (GNU/Linux)

iD8DBQFC4QiODecnbV4Fd/IRAl8BAKDTUzzgP6sKbSLRPJjniyzpT3cWZgCfR6mk
7TWGcp/EburQvaa1C93xLeY=
=8Dme
-----END PGP SIGNATURE-----

---

