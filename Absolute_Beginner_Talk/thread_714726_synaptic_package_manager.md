---
title: "synaptic package manager"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by nishanthaMe on 2008-03-04
when I click on the reload button of the synaptic package manager, it gives a erro saying that could not download all the packages and the erro is following.Please somebody help me to fix the problem

[http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz:](http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz:) 403 Forbidden

---

### Post by PmDematagoda on 2008-03-04
Could you post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by hyper_ch on 2008-03-04
can you

```

ping archive.ubuntu.com

```

---

### Post by nishanthaMe on 2008-03-04
Ping for the archive.ubuntu.com is working and i atached the cat /etc/apt/sources.list here with.


deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by JoshuaRL on 2008-03-04
Try this:
```

gksu gedit /etc/apt/sources.list

```
and post this in:
```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://lk.archive.ubuntu.com/ubuntu/ gutsy universe
# deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://lk.archive.ubuntu.com/ubuntu/ gutsy multiverse
# deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://lk.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

Then go do the following in the terminal after youve saved:
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by nishanthaMe on 2008-03-05
Ok guys, it is working. Thanks a lot

---

