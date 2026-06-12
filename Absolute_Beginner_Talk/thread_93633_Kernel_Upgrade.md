---
title: "Kernel Upgrade?"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by Axeface49 on 2005-11-22
Hello,

I noticed today that the system update icon appeared in the system tray and when i click on it, it lists the linux kernel as an upgradable package.  I was wondering is there anything major that this fixes and are there any dangers in upgrading.

Current Kernel Version: 2.6.12-9-386
Upgraded Version Avalible: 2.6.12.16.1 

Seeing as I don't really feel like messing up my PC I thought I would ask first.
Is it save to just click install? :) 


Hope I posted this in the right place.


Thanks for your help,
Axe Face

---

### Post by Lambert on 2005-11-22
Edit: I was incorrect.

[http://www.ubuntuforums.org/showthread.php?t=93511](http://www.ubuntuforums.org/showthread.php?t=93511)

---

### Post by jamesford on 2005-11-22
i got this too but it wants to upgrade to version 2.6.12-10.....
and ive got only the usual ubuntu repos +  backports

the upgrade went fine tho, no problems. it also grabbed new fxglr drivers and some toher stuff

---

### Post by ed_d on 2005-11-22
No break here, and it fixed my ealier issue of not be able to mount floppies frm the Places>Computer.....

All is fine, remain calm.....

---

### Post by Axeface49 on 2005-11-22
Sources.list:
```

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

# Sun's Java Runtime Environment Repository
deb http://ubuntu.tower-net.de/ubuntu/ breezy java

```

I've attached a screen shot of the update screen thing.

Thanks For Your Help Guys,
Axeface

---

