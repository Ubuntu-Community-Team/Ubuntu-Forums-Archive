---
title: "Error returned from Update manager"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by themainliner on 2007-09-27
Nice easy one (I reckon) I get the following error when running Update Manager:

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://gb.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_GB.bz2: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_GB.bz2: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_GB.bz2: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_GB.bz2: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_GB.bz2: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_GB.bz2: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_GB.bz2: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_GB.bz2: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_GB.bz2: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_GB.bz2: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz: Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

```

Edubuntu 7.04 Feisty Fawn

---

### Post by isaacj87 on 2007-09-27
I had this problem. It's very simple to fix! Just connect to the internet.

Seriously, I had this problem before and I realized it was because I had no connection to my network.

---

