---
title: "Feisty Beta Upgrade"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-03-23
Trying to upgrade to the Feisty Beta

Ran "update-manager -d" and everything went smooth until it finished downloading the files, when i got the error:

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.32-10_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.32-10_all.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.32-10_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.32-10_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/thaifonts-scalable/ttf-thai-tlwg_0.4.5-3_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/thaifonts-scalable/ttf-thai-tlwg_0.4.5-3_all.deb) 404 Not Found


the upgrade then quit. Any way I can get around it? Not like MySQL and Thai fonts are system-essential.

---

### Post by xopher on 2007-03-24
You could try to do a manual: ```
sudo apt-get update; sudo apt-get dist-upgrade
```

and see what that tells you, or as you already have, make note of the packages and install them manually when they are installable. All packages are not always that in development branches ;)

Have fun with Feisty !

---

### Post by nike984 on 2007-03-24
I also upgraded my Edgy to feisty, 2 hours ago.
The upgrade process has shown no error, but after rebooting into feisty,
I've found that the font setting was corrupted.
I've tried several method to solve the problem, but every trial failed.
So, I'm just removing the whole system and installing feisty beta
in a new partition.

---

### Post by sad_iq on 2007-03-24
Feisty is only released as a testing version...so if you upgrade from edgy you will have to modify your sources.list and remove the country code from every line ( [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/)... will have to rename it to  [http://archive.ubuntu.com/ubuntu/...)](http://archive.ubuntu.com/ubuntu/...)). Also you could have problems with external repos(like [http://seveas.imbrandon.com/](http://seveas.imbrandon.com/) )...try disabling them also!!!

---

