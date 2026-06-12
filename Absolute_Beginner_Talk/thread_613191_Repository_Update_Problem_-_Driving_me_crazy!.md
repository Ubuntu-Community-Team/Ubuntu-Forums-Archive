---
title: "Repository Update Problem - Driving me crazy!"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by lauchea2 on 2007-11-14
Ok I have just started to use linux like 3 days ago..
So far it has been nothing but hoops after hoops for me to jump through.

Basically I can get internet connection via wireless but I couldn't get the Synaptic Package Manager to update the list.

No matter what I change for the setting of servers, it just doesn't seem to work. It seems that the server just simply isn't there which I kind of doubt it because the forums' post seem to indicated fine

Or I just simply can't connect to it (Which also doesn't make sense as I can get internet through Firefox)


If anybody can provide me some hope on that, that'll be great. thanks in advance

---

### Post by Dr Small on 2007-11-14
Post the output of:
```
cat /etc/apt/sources.list
```
from Applications > Accessories > Terminal, please.

Dr Small

---

### Post by wolfen69 on 2007-11-14
open terminal:
```
sudo nano /etc/apt/sources.list
```
then copy and paste results back here.

---

### Post by lauchea2 on 2007-11-15
> **Dr Small said:**
> Post the output of:
```
cat /etc/apt/sources.list
```
from Applications > Accessories > Terminal, please.

Dr Small

Output as follows:

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive](ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive) gutsy main universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse



> **wolfen69 said:**
> open terminal:
```
sudo nano /etc/apt/sources.list
```
then copy and paste results back here.

Your command gives the same output

---

### Post by lauchea2 on 2007-11-18
Help anyone? ](*,)

---

### Post by teryowen on 2007-11-18
Same problem, the error i had was when i was installing it said it was gonna skip the security update part during installation since i had no internet connection, and it said it was gonna do it later, but i guess not.

EDIT; i figured it out

Go to Applications -> Add/Remove and then go to Prefrences, and make sure all the 5 check boxes are checked. worked for me! :)

---

