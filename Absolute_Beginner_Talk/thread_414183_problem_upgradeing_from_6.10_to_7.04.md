---
title: "problem upgradeing from 6.10 to 7.04"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by treeby on 2007-04-19
everything downloads and then after like 20 minutes i get this error message:

Failed to fetch [http://malteo.homelinux.net/dists/edgy-malteo/Release.gpg](http://malteo.homelinux.net/dists/edgy-malteo/Release.gpg) Could not connect to malteo.homelinux.net:80 (84.220.197.228). - connect (111 Connection refused)
Failed to fetch [http://malteo.homelinux.net/dists/edgy-malteo/extras/i18n/Translation-en_US.bz2](http://malteo.homelinux.net/dists/edgy-malteo/extras/i18n/Translation-en_US.bz2) Could not connect to malteo.homelinux.net:80 (84.220.197.228). - connect (111 Connection refused)
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)


should i just uninstall automatix and reinstall it after the upgrade?
but what is that malteo.homelinux.net thing?

any help is much much appreciated

thanks!

---

### Post by rocknrolf77 on 2007-04-19
System - administration - software sources : disable all the third party repos. Then you will be good to go :)

---

### Post by konrad_ha on 2007-04-22
That solved all my problems. So simple yet I had to look for it quite a while. This tip should be part of the upgrade instructions. Thanks a lot!

---

