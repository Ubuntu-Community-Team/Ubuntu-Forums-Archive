---
title: "why i cannot connect to Xserver?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by penguinKabuki on 2006-08-14
dear people,
==========
penguin@penguin-desktop:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
penguin@penguin-desktop:~$ sudo -i
Password:
root@penguin-desktop:~# sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
root@penguin-desktop:~#  kdesu kwrite /etc/apt/sources.list
kdesu: cannot connect to X server
root@penguin-desktop:~# kdesu kate /etc/modprobe.d/aliases
kdesu: cannot connect to X server
===========

why?

---

### Post by mcduck on 2006-08-14
Do you have KDE running when you try the last command? kdesu, kwrite and kate are graphical programs and can't be used from console.

If you runing in text mode, try 'sudo nano /etc/apt/sources.list' instead. :)

---

### Post by penguinKabuki on 2006-08-14
thx for the nano command........

when i try to paste this source code.........
=======
## Uncomment the following two lines to fetch updated software from the network
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted 
 ## Uncomment the following two lines to fetch major bug fix updates produced
 ## after the final release of the distribution.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted 
 ## Uncomment the following two lines to add software from the 'universe'
 ## repository.
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse 
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse 
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main 
 deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
 deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
========

how can i save the changes?

---

### Post by red_Marvin on 2006-08-14
If you're in nano you save by pressing Ctrl+O

---

