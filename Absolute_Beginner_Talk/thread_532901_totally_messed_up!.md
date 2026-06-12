---
title: "totally messed up!"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by mozzie on 2007-08-23
well this is a series of (stupid) unfortunate events!
1) i had xp and 98 of different hard drives and used dual boot to switch between them
2) was really keen on geting ubuntu so i installed the first version i could get my hands on(on another hard drive) which is edgy eft
3) downloaded feisty fawn and installed it on the same hard drive
4) turns out this is some wierd console based server edition**oops**
5) tried installing it but i dunno where to begin.....
any help would be appreciated

---

### Post by armandh on 2007-08-23
I muddled my way through that to see what it was all about, and if you really want desktop get [download] the desktop 7.04.

---

### Post by amazingtaters on 2007-08-23
Once you've installed server edition you can install any of the desktop managers, eg

sudo apt-get install ubuntu-desktop

which will dl and install the gnome desktop and everything that comes in a default ubuntu install.

---

### Post by southernman on 2007-08-23
You've got a good start to a totally lean and mean OS there! ;)

Here is a guide that will walk you through getting a GUI (eg gnome, KDE, XFCE, fluxbox) installed:

[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

Enjoy... YMMV

edited:

If you want to upgrade to Feisty, simply change your /etc/apt/sources.list to look something like mine below:

> 
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe




If you mouse doesn't work on your minimal installation you don't have to type all that info in. Just type in the lines that are not commented out (eg no # in front of them)

---

### Post by mozzie on 2007-08-27
oooooh so is that how it works???
damn thats both weird and amazingly cool.....
such an improvment over windows this operating system is!
just keeps flinging more and more surprises at you!!
thanks guys

---

