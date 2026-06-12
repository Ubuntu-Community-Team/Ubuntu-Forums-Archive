---
title: "Update Manager stalling"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by huzzak on 2007-04-23
My update manager can get to the 78th repository and then it stalls and ceases downloading anything else.  It is a problem that is keeping me from upgrading to Feisty.

When I cancel after it has been stalled for a bit it gives me the following warnings an errors:

---------------------------------------------
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://packages.freecontrib.org/ubuntu/plf/dists/edgy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/Release.gpg)
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/i18n/Translation-en_US.bz2)
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2)
[http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu/edgy/Packages.gz:](http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu/edgy/Packages.gz:) Sub-process gzip returned an error code (1)
[http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2:](http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

------------------------------------------------------
An error occured

The following details are provided:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

-------------------------------------------------------
An error occured

The following details are provided:

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)

--------------------------------------------------------

Any ideas on how I can fix this?

---

### Post by huzzak on 2007-04-24
Well, I erased my sources.list and did a sudo apt-get updates and it seemed to take care of the problem.

---

