---
title: "Enabling 3D Rendering on Nvidia Card"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Rothelgang on 2008-02-09
I'm using a NV28 [GeForce4 Ti 4200 AGP 8x] graphics card. I've been trying for a few hours now to enable 3D rendering on it. I've been looking in the Synaptic Package Manager for the  legacy and newer Nvidia GLX packages. Every time I search them though, nothing shows up. I've gone to the restricted drivers to try and activate the NVIDIA accelerated graphics driver. Only problem is, when I go to enable it I get the error message saying nvidia-glx is not enabled. Not sure how I can find where the glx package is if it wont show up on the package manager. 

 Any help would be appreciated.... Thanks

             I'm also using Gutsy Gibbon version.

---

### Post by spiderbatdad on 2008-02-09
those driver should be there. perhaps your sources are commented out...maybe post your /etc/apt/sources.list

---

### Post by jeffus_il on 2008-02-09
Here is the relevant thread:

[http://ubuntuforums.org/showthread.php?t=582362](http://ubuntuforums.org/showthread.php?t=582362)

---

### Post by Rothelgang on 2008-02-09
This is all I have for Nvidia on the package manager.

---

### Post by spiderbatdad on 2008-02-09
please edit your sources list and uncomment (remove the # sign) to make it look more like mine.```
gksu gedit /etc/apt/sources.list
```
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

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
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

then save and run ```
sudo apt-get update
```

---

### Post by Rothelgang on 2008-02-09
Thanks. That did the trick=)

---

