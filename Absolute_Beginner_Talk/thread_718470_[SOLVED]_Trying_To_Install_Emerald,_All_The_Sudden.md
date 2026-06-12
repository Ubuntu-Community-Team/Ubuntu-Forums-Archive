---
title: "[SOLVED] Trying To Install Emerald, All The Sudden I Have Repository Issues"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-03-08
Hello all.  I have never, ever had a repository issue up till now when I'm trying to install Emerald.  I had it installed once before, about a week back, but then I un-installed it.  I did not have a repository problem then, and I've changed nothing in the sources.list that I know of.  

Anyone have any idea what I can do about the error I'm getting?  See the included screenshot.  Thanks!

---

### Post by corney91 on 2008-03-08
Can you post the output of:
```
cat /etc/apt/sources.list
```

Or check System>Administration>Software Sources and make sure all the repositories are checked.


EDIT: Oh, and what happens if you select libemeraldengine0 and libwnck18 for installation as well?

---

### Post by FreewareFan on 2008-03-08
Sure.  Here's the sources.list :

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt gutsy main

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

# Remastersys
deb http://www.remastersys.klikit.org/repository remastersys/

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
deb http://www.linuxmint.com/repository romeo/
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb http://download.tuxfamily.org/swiftweasel gutsy multiverse

```

System>Administration>Software Sources have all boxes checked, just as always.

When I try to install just libemeraldengine0 it tells me that it can't because the dependency of libwnck18 is not installed.   So, I go and search for libwnck18 in Synaptic, but then it tells me that libwnck22 is already installed, and there is no entry for libwnck18 at all.

---

### Post by seshomaru samma on 2008-03-08
```
deb http://download.tuxfamily.org/3v1deb **feisty** eyecandy deb-src 
\http://download.tuxfamily.org/3v1deb** feisty **eyecandy
```
you have fesity sources in a gutsy machine
get rid of them and run
```
sudo apt-get update
```

however if you already installed stuff from them you might encounter other problems


EDIT: to get rid of the feisty repos run
sudo gedit /etc/apt/sources.list

---

### Post by FreewareFan on 2008-03-08
Instead of removing those two entries, I just commented them out, and did the update.   And you know what?  It worked!!

First, I'd like to Thank You for your help on this issue!!

Second, I'd like to ask you why this worked to resolve the problem?  I want to learn as much as I can about this OS and the way it works, so if you wouldn't mind explaining to me what exactly was wrong, I would appreciate it!!

FwF

---

### Post by corney91 on 2008-03-08
I don't know the technical details but the packages from the feisty repos are different from the gutsy ones. Gutsy packages will likely be more up to date. What probably happened is that you had an older package from the feisty repo instead of a more up-to-date one from the gutsy, which emerald depended on. So you were getting emerald from a new repository and it's dependecies from an older one.
Well, that's what I think would've happened anyway - as I said I don't know the technical details:)

---

### Post by FreewareFan on 2008-03-08
OK, well anyways, thanks to you both for your help!!  Have a good one!

FwF

---

