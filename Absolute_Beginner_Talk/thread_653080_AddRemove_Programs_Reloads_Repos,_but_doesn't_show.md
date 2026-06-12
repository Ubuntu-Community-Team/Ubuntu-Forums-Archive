---
title: "Add/Remove Programs Reloads Repos, but doesn't show the new apps"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Changturkey on 2007-12-29
I have set it to All Available Apps, and the list is very small. Synaptic is updated, however...

---

### Post by arochester on 2007-12-29
Your repositories may not be active. Open a terminal and input> gksudo gedit /etc/apt/sources.list . The copy and paste the results here

---

### Post by Changturkey on 2007-12-29
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse #Added by software-properties
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
```

---

### Post by vovuska on 2007-12-29
got the same problem, just installed ubuntu, never used a linux before :)

---

### Post by hyper_ch on 2007-12-29
can you make a screenshot of this "short list" of applications in Synaptic?

---

### Post by taurus on 2007-12-29
> **vovuska said:**
> got the same problem, just installed ubuntu, never used a linux before :)

Open synaptic, System -> Administration -> Synaptic Package Manager -> Settings -> Repositories, and put a check in front of all of them except the last option, Sources code plus the CDROM in the bottom window.  Close it and click Refresh.  Now, you can install whatever you want from synaptic or from Add/Remove.  Make sure you shutdown synaptic first before you open Add/Remove.

---

### Post by vovuska on 2007-12-29
thank you very much!!! very quick and useful answer for a newby like me :)

---

