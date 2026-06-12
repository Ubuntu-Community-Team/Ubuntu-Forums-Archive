---
title: "[SOLVED] help"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Andrew123 on 2007-10-28
How do i reinstall Ubuntu? the update wont update and the add remove thing wont open too :(

---

### Post by overdrank on 2007-10-28
> **Andrew123 said:**
> How do i reinstall Ubuntu? the update wont update and the add remove thing wont open too :(

Hi and welcome you may want to check and make sure all your repos are activated. You can go to system,administration, software sources.

---

### Post by Andrew123 on 2007-10-28
what do i do when that opens?

---

### Post by overdrank on 2007-10-28
> **Andrew123 said:**
> what do i do when that opens?

Hi and maybe this link will help
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
:KS

---

### Post by Mondoman on 2007-10-28
You can always download the install/live CD image, burn it, and do a fresh install from the CD.

---

### Post by overdrank on 2007-10-28
> **Andrew123 said:**
> what do i do when that opens?

I also see in another post of yours you have a problem in your update. Please post the output of this command in the terminal ```
cat /etc/apt/sources.list
``` In the terminal located under applications, accessories, terminal. There is no need to reinstall.

---

### Post by Andrew123 on 2007-10-28
andrew@andrew-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”
andrew@andrew-desktop:~$

---

### Post by overdrank on 2007-10-28
> **Andrew123 said:**
> andrew@andrew-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
[COLOR="Red"]&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main&#8221;[/COLOR]
andrew@andrew-desktop:~$

Hi remove the quote marks on the last line 
```
gksudo gedit /etc/apt/sources.list
```
Then you should be able to update

---

### Post by Andrew123 on 2007-10-28
It worked, thank you very much!!

---

### Post by overdrank on 2007-10-28
> **Andrew123 said:**
> It worked, thank you very much!!

No problem and glad to hear. If you could mark the thread as solved under the thread tools. Thanks :KS

---

