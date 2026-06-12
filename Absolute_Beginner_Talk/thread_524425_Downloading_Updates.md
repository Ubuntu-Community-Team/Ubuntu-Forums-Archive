---
title: "Downloading Updates"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by sachill on 2007-08-13
Hi 

I am trying to install updates and plugins to play my mp3, mpeg etc., but each time I try to download, I get this error "Could not download all repository indexes"


[http://za.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:](http://za.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:) Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
[http://za.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_ZA.bz2:](http://za.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_ZA.bz2:) Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
[http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_ZA.bz2:](http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_ZA.bz2:) Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
[http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_ZA.bz2:](http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_ZA.bz2:) Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
[http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_ZA.bz2:](http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_ZA.bz2:) Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
[http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_ZA.bz2:](http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_ZA.bz2:) Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
[http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:) Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
[http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_ZA.bz2:](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_ZA.bz2:) Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
[http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_ZA.bz2:](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_ZA.bz2:) Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
[http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_ZA.bz2:](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_ZA.bz2:) Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_ZA.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_ZA.bz2:) Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_ZA.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_ZA.bz2:) Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_ZA.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_ZA.bz2:) Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_ZA.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_ZA.bz2:) Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_ZA.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_ZA.bz2:) Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)

---

### Post by be4truth on 2007-08-13
Stupid question: Is your Internet up?
Is your DNS entry ok?
Check your network settings in SYSTEM/ADMINISTRATION/NETWORK
and come back with some more information

---

### Post by shearn89 on 2007-08-13
Also make sure your not behind a proxy - if you are you'll need to change some settings for apt-get.

---

### Post by zvacet on 2007-08-13
**system>administration>software sources>main server**

Maybe this will help.

---

### Post by Seisen on 2007-08-13
The repositories you have are working fine it has something to do with you network connection.

---

