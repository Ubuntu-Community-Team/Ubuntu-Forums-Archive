---
title: "could not dwld all repos indexes  -  broken?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by musky on 2007-07-23
Dunno what this is about or how to fix? Happens when I try an update at the end. thx

---

### Post by AlexenderReez on 2007-07-23
hm..that is normal situation ...sometimes some repos will give that error..you just need to change download place in software sources ....choose other place,then reload:)

---

### Post by musky on 2007-07-23
> **AlexenderReez said:**
> hm..that is normal situation ...sometimes some repos will give that error..you just need to change download place in software sources ....choose other place,then reload:)

Thx, :) Dunno how to go about this?:redface: Read all the stuff & tried a buncha stuff buuut..:confused: dunno how to fix? :( I think I'm dwldin  from the main joint. Tried the Canuck one but didn't seem to work at all.

Sounds like it may be normal but it also turns into a loop & keeps trying unless I shut down the update. Mebbe that's normal too?  When I click on update manger, a window come up sayin up to date (attached).  Mebbe that means everythin ok? Its when I continue & click check that the other one comes up.

---

### Post by Seisen on 2007-07-23
Post your source list.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by musky on 2007-07-23
> **Seisen said:**
> Post your source list.

```
gksudo gedit /etc/apt/sources.list
```

Thx, that mean just put that in console?  I'll assume yes..

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

---

