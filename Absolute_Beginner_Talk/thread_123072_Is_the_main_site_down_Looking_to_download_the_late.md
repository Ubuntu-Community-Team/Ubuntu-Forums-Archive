---
title: "Is the main site down? Looking to download the latest Ubuntu."
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by Typwn on 2006-01-29
Howdy. I've been trying to download the latest Ubuntu but it seems the website is down. Are there any known mirrors or anything? Thanks.

---

### Post by bscbrit on 2006-01-29
My repos are all working fine - they are mostly UK based.  Depends on which 'main site' you mean.

[QUOTE]

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted

[/QUOTE/

---

### Post by Typwn on 2006-01-29
Thanks for the information, but I was speaking more of [http://www.ubuntulinux.org/download](http://www.ubuntulinux.org/download) to get an iso. ;)

---

### Post by bscbrit on 2006-01-29
I've just checked and I cannot get to it either - perhaps it is swamped, or down for maintenance.

---

### Post by Typwn on 2006-01-29
Thanks, guess I'll stick with Warthog

---

### Post by bscbrit on 2006-01-29
I'm not sure that it works for Warthog, but it certainly works for Hoary.  

Open up your /etc/apt/sources.list

edit each 'warthog' to 'breezy'

Save

Open synaptic, reload, and select 'Mark all Upgrades' and 'Apply'.  Everything that you have installed is upgraded to Breezy.  I've update 4 x Hoary using this method but I haven't tried it with Warthog.

EDIT Advantages:  All your data and settings are maintained intact and you only download what you need - not a full iso.

---

### Post by Typwn on 2006-01-29
Ooh! That's perfect! I think I'll do that :)  Thanks.

---

