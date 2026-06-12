---
title: "[SOLVED] Xubuntu - Add/Remove Problems 30 mion after install"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-03-22
i just loaded xubuntu on this computer. I have installed wine and xubuntu-restricted-extras.
so far that is it. I openeed add/remove and it said the packages are out of date and it is STILL just sitting there like 40 min later.  I have had xubuntu installed less than a hour.

---

### Post by oedha on 2008-03-22
point to repository first ( /etc/apt/sources.list )
then
open terminal then type :
sudo apt-get update
sudo apt-get upgrade

---

### Post by forestpixie on 2008-03-22
Make sure you have repos enabled in software sources and third part software - admin menu maybe , un-enable the cdrom.

If there is no software sources - I don't use xubuntu - open the file for editing 
```
gksudo mousepad /etc/apt/sources.list
```

then do the update as oedha has said 

> point to repository first ( /etc/apt/sources.list )

what does that mean :)

---

### Post by N1N31NCHN41L5 on 2008-03-23
> **oedha said:**
> point to repository first ( /etc/apt/sources.list )
then
open terminal then type :
sudo apt-get update
sudo apt-get upgrade

i tried pointing to the reository and this is wht i got:

josh@xubuntu:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
josh@xubuntu:~$ sudo /etc/apt/sources.list
[sudo] password for josh:
sudo: /etc/apt/sources.list: command not found

---

### Post by N1N31NCHN41L5 on 2008-03-23
> **forestpixie said:**
> Make sure you have repos enabled in software sources and third part software - admin menu maybe , un-enable the cdrom.

If there is no software sources - I don't use xubuntu - open the file for editing 
```
gksudo mousepad /etc/apt/sources.list
```

then do the update as oedha has said 



what does that mean :)


I THINK i disabled the cd so it will check ubuntu sources, i put a # on line 4 in mousepad. this is what it shows now:



# 
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

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


What do you mean by repos enabled - repositories???

do they just need to be listed in software source or does the box neeed to be checked???

---

### Post by Oldsoldier2003 on 2008-03-23
the CD is disabled in sources.list and you have the appropriate repos enabled

---

### Post by N1N31NCHN41L5 on 2008-03-23
Thanz all for your help so far.  When I tried to let add/remove update itself it just kept running and running. But I was able to upodate resources. As i understand it you can only run one such type program at a time, so does that mean even though add/remove was on the screen with the little circle spinning it really wasnt running????

---

### Post by zvacet on 2008-03-23
Try to install with synaptic.

---

