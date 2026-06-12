---
title: "install problems"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by btaf on 2008-02-21
I just recently installed ubuntu after the plethora of problems that windows left me, and now i'm running into a lot of walls. so far, i cant watch any of my old avi files on the default player, so i decided to get vlc since its universal. i went to their website, and every time i enter "sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc" i end up with:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-plugin-vlc: Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5) but it is not going to be installed
  vlc: Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: ttf-dejavu but it is not installable
  vlc-plugin-esd: Depends: vlc-nox but it is not going to be installed
E: Broken packages

Any help?

---

### Post by taurus on 2008-02-21
Do you have all the repos enable in /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by frank002 on 2008-02-21
Have you tried using Synaptic? I installed that way and had no dependency problems.

---

### Post by Cypher on 2008-02-21
You've done the following from the VLC instruction page?
>  Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "universe" repository activated.

---

### Post by spiderbatdad on 2008-02-21
You don't say what version of ubuntu you are using. An older release may be part of the problem as far as meeting dependencies goes. If you are on 7.10, you might run sudo apt-get update...then browse synaptic for the packages you are trying to install. If you installed without a working internet connection, your sources need to be enabled.

---

### Post by btaf on 2008-02-21
taurus:
after putting "cat /etc/apt/sources.list" into the terminal, i get:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

i have no idea what that means

frank002:
i tried synaptic, and after a long list of "to be installed" including a lot of things starting with "lib", i get a window saying "the following packages have unresolvable dependencies", specifically:

vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable
 Depends: ttf-dejavu  but it is not installable

again, im lost on this.

Cypher:
I did everything that their page told me to do, and i have the universe, multiverse, and source code choices selected.

but it still wont install

---

### Post by btaf on 2008-02-21
spiderbatdad:
im using gutsy (7.10, or whatever) and installed with internet, and sudo apt-get update works fine, but doesnt help =(

---

### Post by spiderbatdad on 2008-02-21
all the dependencies you seem to need are in synaptic, so not sure what the problem is. Have you tried going directly to synaptic and installing the dependencies first?

---

### Post by spiderbatdad on 2008-02-21
also...a number of your sources are commented out, ie, canonical and some of the multiverse repos. have a look at this thread to further enable sources...that way synaptic should meet your needs. 
[http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)

---

