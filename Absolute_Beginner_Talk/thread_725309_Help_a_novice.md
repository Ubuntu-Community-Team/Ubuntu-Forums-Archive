---
title: "Help a novice"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by dungeonmas124421 on 2008-03-15
Hi.
Just installed kubuntu 7.10 (as one of my pal had reccomended) but the adept manager is not able to fetch any updates rather it shows a version upgrade to 7.10(I have installed the same version).
In Konsole 

"dungeon@dungeons-desktop:~$ sudo apt-get update
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_IN
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_IN
Reading package lists... Done
dungeon@dungeons-desktop:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

Plz help me out folks.:confused:

---

### Post by deepclutch on 2008-03-15
^enable repositories.go to [http://ubuntuguide.org](http://ubuntuguide.org) for more details.
else.press ALT+F2 to get run dialog ,now "run" below command to open editor:
```
kdesu kate /etc/apt/sources.list 
```
edit the contents to look like the one below(remove "#" for repositories except "deb-src" ones)
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

# Medibuntu - Ubuntu 7.10 "gutsy gibbon"
# GPG key-file: http://packages.medibuntu.org/medibuntu-key.gpg
deb http://packages.medibuntu.org/ gutsy free non-free
# deb-src http://packages.medibuntu.org/ gutsy free non-free

# Seveas&#8217; packages (GPG key: 1135D466)
# GPG key-file: http://mirror.ubuntulinux.nl/1135D466.gpg
deb http://mirror.ubuntulinux.nl gutsy-seveas all
# deb-src http://mirror.ubuntulinux.nl gutsy-seveas all

deb http://ppa.launchpad.net/mozillateam/ubuntu gutsy main

```
now save the editor and exit.now try again.

---

### Post by phidia on 2008-03-15
Do you have any repositories enabled? I don't use KDE much but there is a way to enable the repos though the package manager.
Also apt-get install requires an argument (a package to install) to accomplish anything.

---

### Post by jan quark on 2008-03-15
the posters above are right

you have to enable the software sources to be able to download software from the repositories

check this site for more info on installing:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

