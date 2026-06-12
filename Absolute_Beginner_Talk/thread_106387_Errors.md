---
title: "Errors"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by J_P on 2005-12-20
Hi :)  I am getting error messages when i open synaptic or try and install anything,It has'nt stopped me from installing programmes but pops up and makes me click OK before the install starts :confused: 

Heres the error message:

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by rjwood on 2005-12-20
are you on hoary or breezy?

---

### Post by J_P on 2005-12-20
Breezy

---

### Post by rjwood on 2005-12-20
then just either remove them from  your sources.list or change "hoary' to "breezy' . Just don't make doubles of the lines

---

### Post by J_P on 2005-12-20
Nice one RJ that sorted it! ;)

---

### Post by rjwood on 2005-12-20
Your welcome....Good luck!

---

