---
title: "I had an error while upgrading"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Kedster on 2007-10-19
Well ok i went to upgrade to gusty and then  i thought "i no that i need to install the updates for fiesty " so i did then later i went to upgrade again and then it did some stuff and then while it was PREPARING TO UPGRADE  is seid this

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

```
Failed to fetch http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)

```
what do i do now

---

### Post by linuxwizard on 2007-10-19
Try removing or disable extra repos you added to your source list. Than try upgrade again

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by Kedster on 2007-10-26
ok welll then this happended
```
Can't guess meta-package

Your system does not contain a ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or edubuntu-desktop package and it was not possible to detect which version of Ubuntu you are running.
 Please install one of the packages above first using synaptic or apt-get before proceeding.
```
 
 then this
```
Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

```

---

### Post by Kedster on 2007-10-26
am i the ony one whos had this problem  or have any of u had it

---

### Post by Maestro23 on 2007-10-26
> **Kedster said:**
> am i the ony one whos had this problem  or have any of u had it

Can you post your /etc/apt/sources.list

> cat /etc/apt/sources.list

---

### Post by Kedster on 2007-10-26
# 
# deb cdrom:[Edubuntu 7.04 _Feisty Fawn_ - Release i386 Binary-1 (20070415)]/ feisty main restricted

# deb cdrom:[Edubuntu 7.04 _Feisty Fawn_ - Release i386 Binary-1 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe
# deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
# deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
# deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
# deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
# deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

---

### Post by Kedster on 2007-10-26
please

---

### Post by ebeard on 2007-10-26
I cant upgrade my laptop today either, get a similar error. I assumed it's server issue. Worked fine on my desktop a few days ago.

---

### Post by Kedster on 2007-10-27
well atleast im not the only one  if u find a fix can u post it ill do the same

---

