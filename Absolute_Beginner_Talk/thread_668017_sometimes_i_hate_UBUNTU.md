---
title: "sometimes i hate UBUNTU"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by patchido on 2008-01-14
i really love ubuntu but well.... when it gets to working the same as windows it disapoints me sometimes... there are some things i cant see in some web pages.. they say i am missing java or stuff like that then i install it.. reboot firefox.. or even ubuntu .. and i am still missing it... any suggestions on what to do??? also video codecs

---

### Post by PmDematagoda on 2008-01-14
Concerning your Java, post the result of:
```
sudo update-alternatives --config java
```

Concerning the codecs, post the result of:-
```
cat /etc/apt/sources.list
```

---

### Post by nikoPSK on 2008-01-14
video codecs for like .mov files? Just open up totem and it will ask you to install em and bring you to em.

nikoPSK

---

### Post by CCNA_student on 2008-01-15
I have instructions here at [http://wheatlandlinux.wordpress.com/instructions-and-how-tos/]("http://wheatlandlinux.wordpress.com/instructions-and-how-tos/").
I hope that these instructions work for you.

        Sin Cere,

        CCNA

---

### Post by patchido on 2008-01-15
```
pato@pato-laptop:~$ sudo update-alternatives --config java
[sudo] password for pato:

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/bin/gij-4.2
          2    /usr/bin/cacao

Press enter to keep the default[*], or type selection number: 
pato@pato-laptop:~$ 



pato@pato-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mx.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
pato@pato-laptop:~$ 

```

---

### Post by CCNA_student on 2008-01-15
In the Add/Remove thing type in Java and make sure all Software is available.

---

### Post by PmDematagoda on 2008-01-15
Execute:-
```
sudo apt-get install sun-java6-jre sun-java6-bin
```
After that, execute:-
```
sudo update-alternatives --config java
```

About your codecs, you can do what nikoPSK said, open a video file in Totem, you will then be asked if you want to install the codecs.

---

### Post by patchido on 2008-01-15
what about .rm videos?

---

### Post by PmDematagoda on 2008-01-15
For .rm videos you will have to get Real Player for Linux.

---

