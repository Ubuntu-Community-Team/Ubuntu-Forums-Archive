---
title: "Bad header line"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by saltscar on 2006-04-24
Please help a newbie to Linux and Ubuntu.  I get this message when I try to install an auto update.  I get:
Problems found
W: Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.12~winehq1-1_i386deb](http://wine.sourceforge.net/apt/binary/wine_0.9.12~winehq1-1_i386deb)
Bad header line
How do I clear this problem?

---

### Post by earobinson on 2006-04-24
could you post your /etc/apt/sources.list, it looks like you have some bad reops

---

### Post by saltscar on 2006-04-24
My souce list

#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

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
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe multiverse main restricted

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
#deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

#deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

#deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## created by arniemaxremoved
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

---

### Post by earobinson on 2006-04-24
simple problem is that the wine package your computer is trying to axcess no longer exists, try to uninstall and reinstall.

If you follow the link W: Failed to fetch [http://wine.sourceforge.net/apt/bina...ehq1-1_i386deb](http://wine.sourceforge.net/apt/bina...ehq1-1_i386deb) you will see that it is not a .deb file which is weird to me, but the .deb equivelent exists.

---

### Post by saltscar on 2006-04-24
Many thanks for your help.  Problem solved.

---

