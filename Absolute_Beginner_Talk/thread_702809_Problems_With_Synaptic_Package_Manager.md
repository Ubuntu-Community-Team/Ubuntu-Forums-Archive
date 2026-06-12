---
title: "Problems With Synaptic Package Manager"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by rl44 on 2008-02-20
I'm a complete beginner to using Linux.  When I try to use the Synaptic Package Manager, I get this error, "E: Type 'wget' is not known on line 82 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

---

### Post by spiderbatdad on 2008-02-20
[http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)

---

### Post by seventhc on 2008-02-20
could you post the output of this
```
cat /etc/apt/sources.list
```

---

### Post by rl44 on 2008-02-20
Here's what I got after typing that in

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-updates main restricted
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy universe restricted main
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy universe multiverse #Added by software-properties
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-security main restricted universe
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-security restricted main multiverse universe #Added by software-properties
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted universe multiverse
#AUTOMATIX REPOS END
wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O-


deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
ross@RossLaptop:~$

---

### Post by seventhc on 2008-02-20
This line 82
It is right after  
#AUTOMATIX REPOS END
like 3rd line from the bottom.
```
wget http://packages.dfreer.org/7572013D.gpg -O-
```I forgot to ask, but what are you trying to install?
I would probably try commenting that line out.
open a terminal and paste this in
```
gksu gedit /etc/apt/sources.list
```and make that line look like this
```

# wget http://packages.dfreer.org/7572013D.gpg -O-

```then save it then open a terminal and run
```

sudo apt-get update
```then try again.

---

### Post by seventhc on 2008-02-20
Here's what mine looks like.
```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

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
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

