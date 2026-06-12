---
title: "Another one more on server"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by camellito on 2007-06-13
Hi all, i have a big proble here!!

I need to install gnome in ubuntu server 7.04 without Internet, but with ubuntu desktop 7.04 livecd:

1.- $sudo nano /etc/apt/sources.list

I commented all the line less "deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted"

[COLOR="Gray"]#
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse[/COLOR]

Ctrol+o - Ctrol+x...

2.- $sudo apt-cdrom add (It's Ok)

3.- $sudo apt-get update (It's Ok)

4.- $sudo apt-get install x-window-system-core gnome-core

Reading package lists... done
Building dependency tree
Reading state information ... done
E: Couldn't find package x-window-system-core

It does not work with any $sudo apt-get install commands.

Please Helpme!!!

Sorry for my bad inglish :S, thanks.

---

### Post by zvacet on 2007-06-13
I don´t think you can install from live Cd but command is

```
sudo aptitude install ubuntu-desktop
```

---

### Post by camellito on 2007-06-13
zvacet, thanks for your answer, but not work with any "install" command.

Like:

$sudo apt-get install x-window-system-core gnome-core
$sudo apt-get install x-window-system gdm
$sudo apt-get install xserver-xorg
$sudo apt-get install ubuntu-desktop
$sudo apt-get install xubuntu-desktop
$sudo apt-get install kubuntu-desktop

All say:

[COLOR="DimGray"]Reading package lists... done
Building dependency tree
Reading state information ... done
E: Couldn't find package x-window-system-core
E: Couldn't find package x-window-system
E: Couldn't find package xserver-xorg
E: Couldn't find package ubuntu-desktop
E: Couldn't find package xubuntu-desktop
E: Couldn't find package kubuntu-desktop[/COLOR]

**I must think that nobody could install it this way?**

Please, I need help guys... this is very important for me. Thanks.

***Edit: does not work with $sudo aptitude install "command"***

---

### Post by zvacet on 2007-06-13
Once again,you can not install ubuntu-desktop from live Cd.You need alternate Cd for that or download it from comp with internet connection(it is not small download),burn on CD and install on your comp.Here is link

[http://packages.ubuntu.com/feisty/metapackages/ubuntu-desktop]("http://packages.ubuntu.com/feisty/metapackages/ubuntu-desktop")

Install first packages marked with red ball(they are dependencies).

---

