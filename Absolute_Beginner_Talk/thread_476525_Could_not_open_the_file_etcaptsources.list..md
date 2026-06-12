---
title: "Could not open the file /etc/apt/sources.list."
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by maitresse on 2007-06-17
apparently i dont have permission.  i cant use add/remove until i get this sorted.  

any ideas?

---

### Post by JAPrufrock on 2007-06-17
sudo gedit /etc/apt/sources.list

---

### Post by starcraft.man on 2007-06-17
> **maitresse said:**
> apparently i dont have permission.  i cant use add/remove until i get this sorted.  

any ideas?

Have to use sudo to edit it manually. Here is the command you want:

```
gksudo gedit /etc/apt/sources.list
```

Just a note, when opening graphical applications with the terminal and enabling with root, use gksudo on Ubuntu. When its a command operation in the terminal standard sudo will do. Sudo usually works with graphical apps, it is just good practice to get into. Just make sure you know what your doing before editing the list.

---

### Post by sessine on 2007-06-17
The sources.list file should be readable by anyone.  open a terminal and post the result of ```
ls -l /etc/apt
``` (note the -l is a lowercase L)

---

### Post by maitresse on 2007-06-17
> **sessine said:**
> The sources.list file should be readable by anyone.  open a terminal and post the result of ```
ls -l /etc/apt
``` (note the -l is a lowercase L)


this is what i get!

karen@ubuntu:~$ ls -l /etc/apt
total 48
drwxr-xr-x 2 root root 4096 2006-09-21 21:49 apt.conf.d
-rw------- 1 root root    0 2006-01-31 20:27 secring.gpg
-rw------- 1 root root 2195 2007-06-16 11:30 sources.list
-rw------- 1 root root 2250 2006-03-19 11:57 sources.list~
-rw-r--r-- 1 root root 1868 2006-01-31 20:42 sources.list_backup_200601312117
-rw-r--r-- 1 root root 2152 2006-01-31 21:17 sources.list_backup_200601312142
-rw------- 1 root root 2264 2007-04-09 15:03 sources.list_backup_200704151051
drwxr-xr-x 2 root root 4096 2006-04-18 20:47 sources.list.d
-rw------- 1 root root 2256 2006-09-21 19:52 sources.list.distUpgrade
-rw------- 1 root root 2195 2007-06-16 11:30 sources.list.save
-rw------- 1 root root 1200 2006-01-31 20:27 trustdb.gpg
-rw-r--r-- 1 root root 2393 2006-01-31 20:27 trusted.gpg
-rw-r--r-- 1 root root 2381 2006-01-31 20:27 trusted.gpg~
karen@ubuntu:~$

---

### Post by maitresse on 2007-06-17
> **starcraft.man said:**
> Have to use sudo to edit it manually. Here is the command you want:

```
gksudo gedit /etc/apt/sources.list
```

Just a note, when opening graphical applications with the terminal and enabling with root, use gksudo on Ubuntu. When its a command operation in the terminal standard sudo will do. Sudo usually works with graphical apps, it is just good practice to get into. Just make sure you know what your doing before editing the list.
this is what i get

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
## created by arniemaxremoved

---

### Post by maitresse on 2007-06-17
bump

---

### Post by schorsch on 2007-06-17
```
sudo chmod 0644 /etc/apt/sources.list
```

---

### Post by maitresse on 2007-06-17
> **schorsch said:**
> ```
sudo chmod 0644 /etc/apt/sources.list
```

what is that supposed to do?

---

### Post by schorsch on 2007-06-17
... that the file gets the follwing permissions:

```
-rw-r--r-- 1 root root 2195 2007-06-16 11:30 sources.list
```

... read/write for the user, read for the group and read for the rest of the world. Right at the moment the file is only readable by root.

---

### Post by Mudit_BITS on 2008-02-29
Failed to fetch [http://elisa.fluendo.com/packages/dists/gutsy/main/binary-i386/Packages.gz](http://elisa.fluendo.com/packages/dists/gutsy/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://www.virtualbox.org/debian/dists/gutsy/non-free/binary-i386/Packages.gz](http://www.virtualbox.org/debian/dists/gutsy/non-free/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://ppa.launchpad.net/zachtib/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://ppa.launchpad.net/zachtib/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://e17.dunnewind.net/ubuntu/dists/gutsy/e17/binary-i386/Packages.gz](http://e17.dunnewind.net/ubuntu/dists/gutsy/e17/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://ppa.launchpad.net/zachtib/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://ppa.launchpad.net/zachtib/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://ubuntu.davromaniak.eu/dists/gutsy-depomaniak/all/source/Sources.gz](http://ubuntu.davromaniak.eu/dists/gutsy-depomaniak/all/source/Sources.gz)  403 Forbidden
Failed to fetch [http://packages.ryanak.ca/dists/ryan-gutsy/all/source/Sources.gz](http://packages.ryanak.ca/dists/ryan-gutsy/all/source/Sources.gz)  403 Forbidden
Failed to fetch [http://ubuntu.iuculano.it/dists/gutsy/all/source/Sources.gz](http://ubuntu.iuculano.it/dists/gutsy/all/source/Sources.gz)  403 Forbidden
Failed to fetch [http://mirror.ubuntulinux.nl/dists/gutsy-seveas/all/binary-i386/Packages.gz](http://mirror.ubuntulinux.nl/dists/gutsy-seveas/all/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://pkg-voip.buildserver.net/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://pkg-voip.buildserver.net/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.gz](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://www.telemail.fi/mlind/ubuntu/dists/feisty/fonts/binary-i386/Packages.gz](http://www.telemail.fi/mlind/ubuntu/dists/feisty/fonts/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-i386/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/gutsy/all/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/gutsy/all/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://mirror.ubuntulinux.nl/dists/gutsy-seveas/all/source/Sources.gz](http://mirror.ubuntulinux.nl/dists/gutsy-seveas/all/source/Sources.gz)  403 Forbidden
Failed to fetch [http://www.telemail.fi/mlind/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://www.telemail.fi/mlind/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://www.telemail.fi/mlind/ubuntu/dists/feisty/fonts/source/Sources.gz](http://www.telemail.fi/mlind/ubuntu/dists/feisty/fonts/source/Sources.gz)  403 Forbidden
Failed to fetch [http://snapshots.ekiga.net/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://snapshots.ekiga.net/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://au.ubuntu.cafuego.net/dists/gutsy-cafuego/all/binary-i386/Packages.gz](http://au.ubuntu.cafuego.net/dists/gutsy-cafuego/all/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://repository.debuntu.org/dists/gutsy/multiverse/binary-i386/Packages.gz](http://repository.debuntu.org/dists/gutsy/multiverse/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/gutsy/all/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/gutsy/all/source/Sources.gz)  403 Forbidden
Failed to fetch [http://snapshots.ekiga.net/ubuntu/dists/gutsy/main/source/Sources.gz](http://snapshots.ekiga.net/ubuntu/dists/gutsy/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://cl.naist.jp/~eric-n/ubuntu-nlp/dists/gutsy/all/binary-i386/Packages.gz](http://cl.naist.jp/~eric-n/ubuntu-nlp/dists/gutsy/all/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/gutsy/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://deb.opera.com/opera/dists/etch/non-free/binary-i386/Packages.gz](http://deb.opera.com/opera/dists/etch/non-free/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/gutsy/free/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://www.mpe.mpg.de/~ach/kubuntu/gutsy/./Packages.gz](http://www.mpe.mpg.de/~ach/kubuntu/gutsy/./Packages.gz)  403 Forbidden
Failed to fetch [http://cl.naist.jp/~eric-n/ubuntu-nlp/dists/feisty/all/source/Sources.gz](http://cl.naist.jp/~eric-n/ubuntu-nlp/dists/feisty/all/source/Sources.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.czessi.net/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://archive.czessi.net/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/main/source/Sources.gz](http://wine.budgetdedicated.com/apt/dists/gutsy/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/main/source/Sources.gz](http://ubuntu.beryl-project.org/dists/edgy/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://www.mpe.mpg.de/~ach/kubuntu/gutsy/./Sources.gz](http://www.mpe.mpg.de/~ach/kubuntu/gutsy/./Sources.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.czessi.net/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://archive.czessi.net/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.czessi.net/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://archive.czessi.net/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.czessi.net/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://archive.czessi.net/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.czessi.net/ubuntu/dists/gutsy/preview/binary-i386/Packages.gz](http://archive.czessi.net/ubuntu/dists/gutsy/preview/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.czessi.net/ubuntu/dists/gutsy/main/source/Sources.gz](http://archive.czessi.net/ubuntu/dists/gutsy/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.czessi.net/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://archive.czessi.net/ubuntu/dists/gutsy/restricted/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.czessi.net/ubuntu/dists/gutsy/universe/source/Sources.gz](http://archive.czessi.net/ubuntu/dists/gutsy/universe/source/Sources.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.czessi.net/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://archive.czessi.net/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.czessi.net/ubuntu/dists/gutsy/preview/source/Sources.gz](http://archive.czessi.net/ubuntu/dists/gutsy/preview/source/Sources.gz)  403 Forbidden
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/source/Sources.gz](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/source/Sources.gz)  403 Forbidden
Failed to fetch [http://www.telemail.fi/mlind/ubuntu/dists/feisty/main/source/Sources.gz](http://www.telemail.fi/mlind/ubuntu/dists/feisty/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/source/Sources.gz)  403 Forbidden
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
tool@tool-desktop:/etc/apt$ 



I GET THIS WHEN I RUN sudo apt-get update can any 1 help please its urgent :confused:

---

### Post by philinux on 2008-02-29
you would have been better starting your own thread with your system specs and the nature of the problem.

Post the output of

cat /etc/apt/sources.list

---

### Post by Mudit_BITS on 2008-02-29
# mudit's Ubuntu Gutsy Gibbon 7.10 Sources list
#
# Repository List based on standard gutsy with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
# wget -q URL -O- | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
# sudo apt-key add FILE

# Ubuntu supported packages (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy restricted main multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates restricted main multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy restricted main multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates restricted main multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse

# Ubuntu community supported packages (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports restricted main multiverse universe

# Ubuntu Proposed packages (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe

#Canonical Commercial Repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# UbuntuStudio Repository (GPG key: B6A4EB33)
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) gutsy main
deb-src [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) gutsy main

# Bleeding edge wine packages
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

# Seveas’ packages (GPG key: 1135D466)
# GPG key-file: [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg)
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) gutsy-seveas all
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) gutsy-seveas all

# Upstream Opera (GPG key: 6A423791)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

# Upstream Beryl (GPG key: ed8a569e)
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb-src [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

# Medibuntu - Ubuntu 7.10 "gutsy gibbon"
# GPG key-file: [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

# The repository from Kubuntu Germany
# GPG key-file: [http://archive.czessi.net/ubuntu/kczessi.gpg](http://archive.czessi.net/ubuntu/kczessi.gpg)
deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) gutsy restricted main multiverse preview universe
deb-src [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) gutsy restricted main multiverse preview universe

# Achim’s Unofficial ‘gutsy’ Kubuntu packages
# GPG key-file: [http://www.mpe.mpg.de/~ach/ach-gpg.asc](http://www.mpe.mpg.de/~ach/ach-gpg.asc)
deb [http://www.mpe.mpg.de/~ach/kubuntu/gutsy](http://www.mpe.mpg.de/~ach/kubuntu/gutsy) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/gutsy](http://www.mpe.mpg.de/~ach/kubuntu/gutsy) ./

# Ekiga and Debian pkg-voip
deb [http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) gutsy main

# Ubuntu repository for Screenlets (GPG key: F854AFD7)
# GPG key-file: [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg)
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets
deb-src [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets

# Subpixel Font rendering packages (GPG key: 937215FF)
# Improved fonts on LCDs - WARNING: May violate some patents
# GPG key-file: [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg)
deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty main fonts
deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty main fonts

# Skype packages
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

# gnomemeeting - ekiga (GPG key: 52ABFCB1)
deb [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) gutsy main
deb-src [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) gutsy main

# Cafuego’s feisty Stuff: Broadcom firmware, google-earth, secondlife
deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) gutsy-cafuego all
deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) gutsy-cafuego all

# Debuntu Ubuntu gutsy packages
# GPG Key: [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt)
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multivers

# Automatix Repo
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

# The Ubuntu NLP Repository (GPG key: 8ABD1965)
# GPG key-file: [http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg](http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg)
deb [http://cl.naist.jp/~eric-n/ubuntu-nlp](http://cl.naist.jp/~eric-n/ubuntu-nlp) gutsy all
deb-src [http://cl.naist.jp/~eric-n/ubuntu-nlp](http://cl.naist.jp/~eric-n/ubuntu-nlp) feisty all

# syzygy42 repository: avant-window-navigator, exaile, closure… (GPG key: 8434D43A)
# GPG key-file: [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg)
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy all
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy all

## Swiftfox (enhanced Firefox for linux) packages
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

# Le dépomaniak repository (GPG key: 1D59E694)
# GPG key-file: [http://ubuntu.davromaniak.eu/1D59E694.gpg](http://ubuntu.davromaniak.eu/1D59E694.gpg)
deb [http://ubuntu.davromaniak.eu](http://ubuntu.davromaniak.eu) gutsy-depomaniak all
deb-src [http://ubuntu.davromaniak.eu](http://ubuntu.davromaniak.eu) gutsy-depomaniak all

# Ryan Kavanagh’s packages (GPG key: 02544D0E)
# GPG key-file: [http://packages.ryanak.ca/02544D0E.gpg](http://packages.ryanak.ca/02544D0E.gpg)
deb [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-gutsy all
deb-src [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-gutsy all

# Iuculano’s debian packages (GPG key: AE3BE9AA)
# GPG key-file: [http://ubuntu.iuculano.it/AE3BE9AA.gpg](http://ubuntu.iuculano.it/AE3BE9AA.gpg)
deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) gutsy all
deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) gutsy all

# Elisa Debian Packages
# GPG key-file: [http://elisa.fluendo.com/packages/philn.asc](http://elisa.fluendo.com/packages/philn.asc)
deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) gutsy main

# Virtualbox PUEL
# GPG key-file: [http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc)
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

#Deluge
deb [http://ppa.launchpad.net/zachtib/ubuntu](http://ppa.launchpad.net/zachtib/ubuntu) gutsy universe main

## Elbuntu
# GPG key-file: [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc)


deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) gutsy e17

---

### Post by philinux on 2008-02-29
Wholly crap you got enough sources. 

Anyway it looks ok.

I'd go into system admin Software Sources and select a different server. 

Other than that you could comment out one at a time starting with the non ubuntu ones and see if it's one of them that has a server down.

---

### Post by Mudit_BITS on 2008-02-29
I want to know what is this 403 forbidden error?
why am i getting this?

---

### Post by jan quark on 2008-02-29
just as a side note

i see automatix in your sources list

[B]please do not use automatix
it is not recommend by me and other advanced users I know
automatix  can cause heavy compatibility issues[/B]

---

### Post by ashmew2 on 2008-02-29
I agree with Jan Quark...Automatix has reportedly caused havoc...

---

