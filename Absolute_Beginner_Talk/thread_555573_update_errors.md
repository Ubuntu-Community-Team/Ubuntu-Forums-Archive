---
title: "update errors"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-09-20
Hi,
The following is the error of command sudo apt-get update(ofcourse after the regular repository check).
Can anyone tell me whats the problem?
Thanks.

> W: GPG error: [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release: Unknown error executing gpgv
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: Unknown error executing gpgv
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release: Unknown error executing gpgv
W: GPG error: [http://www.telemail.fi](http://www.telemail.fi) feisty Release: Unknown error executing gpgv
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release: Unknown error executing gpgv
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: Unknown error executing gpgv
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: Unknown error executing gpgv
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release: Unknown error executing gpgv
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release: Unknown error executing gpgv
W: GPG error: [http://mirror.noreply.org](http://mirror.noreply.org) feisty Release: Unknown error executing gpgv
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release: Unknown error executing gpgv
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release: Unknown error executing gpgv


---

### Post by ukripper on 2007-09-20
Can you post your sources.list here -
```
sudo gedit /etc/apt/sources.list
```

---

### Post by gupta_sumesh63 on 2007-09-20
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

This is my sources.list


> deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security multiverse
deb [http://archive.ubuntustudio.org/ubuntustudio/](http://archive.ubuntustudio.org/ubuntustudio/) feisty main
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs... 
# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
# deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) feisty main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) feisty main


#AUTOMATIX REPOS START


deb [http://www.getautomatix.com/apt/](http://www.getautomatix.com/apt/) feisty main

deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

# deb [http://www.bunkus.org/ubuntu/feisty/](http://www.bunkus.org/ubuntu/feisty/) ./
# deb-src [http://www.bunkus.org/ubuntu/feisty/](http://www.bunkus.org/ubuntu/feisty/) ./
# deb [http://falcon.landure.fr](http://falcon.landure.fr) feisty pidgin
# deb-src [http://falcon.landure.fr](http://falcon.landure.fr) feisty pidgin







# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
# deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

---

### Post by gupta_sumesh63 on 2007-09-21
bump!!!

---

### Post by mysticmatrix on 2007-09-21
Well the best I can guess is that either Automatix or Gutsy repos have broken up the PGP programme used by Ubuntu to check whether your downloaded application is authentic or not. This would not be a great problem in general, but could compromise security sometime?

BTW, why did you need AUTOMATIX? One of the worst apps I have ever seen.

---

### Post by ukripper on 2007-09-21
Did you do recent upgrade from edgy to feisty?

---

### Post by gupta_sumesh63 on 2007-09-22
Nope. I have a clean install of feisty. I upgraded the kernel to 2-6-22-10. Could that be the problem?

---

### Post by ukripper on 2007-09-22
try switching back to previous kernel...choose during Grub screen

---

### Post by alienexplorers on 2007-09-22
Get rid of Automatix.  Nothing but problems with that junk software.  Use the following page to get a good sources.lst
> [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

