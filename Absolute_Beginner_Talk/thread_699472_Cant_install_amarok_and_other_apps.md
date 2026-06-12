---
title: "Cant install amarok and other apps"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-02-17
I cant install Amarok and most of other apps cuz it says my computer type i386 aint supported...wadda i do

---

### Post by sb12 on 2008-02-17
> **munch3 said:**
> I cant install Amarok and most of other apps cuz it says my computer type i386 aint supported...wadda i do

if that error means what I think it means you need to buy a newer computer

---

### Post by jan quark on 2008-02-17
pls

post the output from this command
```

cat /etc/apt/sources.list
```

it might be your sources are commented out

---

### Post by munch3 on 2008-02-17
jovan@jovan-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main
jovan@jovan-desktop:~$

---

### Post by jan quark on 2008-02-17
go to 

system > administration > software sources

and enable all software sources except the cd
then reload and try to install again

---

### Post by munch3 on 2008-02-17
U gonna have to refine that a bit, 
under ''installable from CD/DVD rom  I only got ''cdrom with ubuntu gutsy gibbon 7.10

---

### Post by munch3 on 2008-02-17
erm...noooo my computer is fine, actually its much more than fine its excellent :)

---

### Post by munch3 on 2008-02-17
THANK YOU GOD!!!
You've single handedly solved all my problems!I just ticked all of em stuff, and am installing  Amarok right now.Can u just tell me which one is not supposed 2 b ticked

---

