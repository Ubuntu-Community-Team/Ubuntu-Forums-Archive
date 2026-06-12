---
title: "[SOLVED] low graphics mode|no sound|gpg pub key error"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by hrolen on 2008-04-06
I update regularly on my darter which is running ubuntu 7.10.  The most recent updates threw my laptop into low graphics mode with no sound.  I've been searching the ubuntu forum and have tried a few fixes but to no avail, and  when I run sudo apt-get update  I get the GPG pubkey error for planet76.com

any suggestions would be appreciated.
HR

---

### Post by greenstar on 2008-04-06
Post the output of ```
cat /etc/apt/sources.list
```

---

### Post by hrolen on 2008-04-06
## Ubuntu 7.04 System76 Repositories Listing

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse #Added by software-properties


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security restricted main universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe

## System76 Driver Repository
deb [http://planet76.com/repositories/](http://planet76.com/repositories/) ./

---

### Post by greenstar on 2008-04-06
Backup your sources.list:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.original
```Open sources.list for editing:
```
sudo gedit /etc/apt/sources.list
```Comment out the last line by changing:
```
## System76 Driver Repository
deb [http://planet76.com/repositories/](http://planet76.com/repositories/) ./
```to:
```
## System76 Driver Repository
## deb [http://planet76.com/repositories/](http://planet76.com/repositories/) ./
```Then update your packages:
```
sudo aptitude update
```Then you can run this to try and let aptitude sort out the problem:
```
sudo aptitude -f install
```This one might help by configuring any unconfigured packages:
```
sudo dpkg-reconfigure -a
```This one might help by upgrading your packages to current:
```
sudo aptitude safe-upgrade
``` then ```
sudo aptitude dist-upgrade
``` HTH,

Greenstar

---

### Post by hrolen on 2008-04-06
Thank you very much!  I think that took care of the low graphics mode error.  The sound has not been restored, so I'm still working on that one.

---

### Post by greenstar on 2008-04-07
Glad I could help with at least part of the problem. I'm afraid I can't do as much with sound.

Maybe someone else will be able to help with that one.

Greenstar

---

