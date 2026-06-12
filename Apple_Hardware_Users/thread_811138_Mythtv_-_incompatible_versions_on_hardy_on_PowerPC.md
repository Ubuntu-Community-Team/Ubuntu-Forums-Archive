---
title: "Mythtv - incompatible versions on hardy on PowerPC"
date: 2008-05-28
forum: Apple Hardware Users
---

### Post by terevos on 2008-05-28
I can't seem to install mythtv on hardy heron on powerpc.

The mythtv-common package lists its version as '0.21.0+fixes16838-0ubuntu3'.
The mythtv-frontend package lists its version as '0.21.0-0ubuntu2'

mythtv-common is a dependency of mythtv-frontend, but the versions are incompatible with each other.

Is there something I'm missing here? Or are the packages for mythtv on hardy on powerpc truly broken?

---

### Post by genepool on 2008-05-29
I'm having the same problem on a powerbook g4.  Here is my /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release powerpc (20080424.1)]/ hardy main
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ports.ubuntu.com/ubuntu-ports/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ports.ubuntu.com/ubuntu-ports/ hardy universe
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ hardy multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://ports.ubuntu.com/ubuntu-ports/ hardy-security main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-security universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-security multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-security multiverse

deb http://ppa.launchpad.net/tualatrix/ubuntu gutsy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu gutsy main

```

---

### Post by terevos on 2008-05-29
bump

---

### Post by genepool on 2008-06-02
I guess we just have to wait for the repo's to get sorted out since we seem to be the only ones who care:(

---

