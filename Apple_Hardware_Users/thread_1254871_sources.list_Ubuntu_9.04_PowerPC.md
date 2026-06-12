---
title: "sources.list Ubuntu 9.04 PowerPC"
date: 2009-08-31
forum: Apple Hardware Users
---

### Post by wbb on 2009-08-31
I somehow messed up my Ubuntu 9.04 PowerPC software sources list.
Can someone please post the default sources.list for me?
I promise I will make a backup before I start playing with it again.

---

### Post by cptfx on 2009-09-06
Here you go.  Not sure if actually posting the contents was good etiquette or not.  My apologies if it's not.

```
# 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release powerpc (20090421)]/ jaunty main restricted
deb-src http://ports.ubuntu.com/ jaunty restricted main #Added by software-properties

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release powerpc (20090421)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ports.ubuntu.com/ubuntu-ports/ jaunty main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-updates main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty universe
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-security main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ jaunty-security restricted main multiverse universe #Added by software-properties
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-security multiverse

```

---

### Post by cptfx on 2009-09-10
Funny story.  I just screwed up my sources.list too.  Glad I posted it

---

