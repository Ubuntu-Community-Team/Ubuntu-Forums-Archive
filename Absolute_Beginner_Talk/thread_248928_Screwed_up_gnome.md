---
title: "Screwed up gnome"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by GuitarHero on 2006-09-01
Following this thread
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)
 I did these commands:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 
sudo apt-get install linux-sound-base alsa-base alsa-utils 
and because those commands removed gdm and ubuntu-desktop I did this as reccomended:
sudo apt-get install gdm ubuntu-desktop

I rebooted and my sound problems were not fixed, but even worse was it bootewd into the xubuntu splash screen( i have xfce installed also ).  I chose to boot into gnome but some things arent right.  gnome-terminal is gone!  Luckily I have the xfce terminal as well.  So i did sudo apt-get install gnome-terminal, and i got this:
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (= 2.14.1-0ubuntu1) but 2.14.2-0ubuntu3 is to be installed
E: Broken packages
I tried installing gnome-terminal-data but that didnt do it.  Ive also tried installing gdm and ubuntu-desktop again.  Nothing fixes it.

---

### Post by pyros on 2006-09-01
I could definiatly be wrong, but it sounds like you may have lost an entry to your source.list

---

### Post by GuitarHero on 2006-09-01
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
# or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main



how do i know whats missing?

---

### Post by GuitarHero on 2006-09-01
I still need help, is there a way to reinstall gnome and fix all of this?

---

### Post by pyros on 2006-09-02
I don't know, man. I would try renaming sources.list and creating a blank one. Then run apt-get update against the blank list, replace the blank with the original list and running apt-get update again. See if you still have unresolved deps.

---

