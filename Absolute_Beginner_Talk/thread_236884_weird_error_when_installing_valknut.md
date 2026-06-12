---
title: "weird error when installing valknut"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2006-08-15
in synaptic package manager > settings > repositories, ive added the universe and multiverse options to get those "ubuntu supported packages" but when im trying to mark valknut for installation i get [this]("http://img53.imageshack.us/img53/3852/screenshottr9.png") error. i guess i have to install are those packages but there are too many and each packages has its own dependecies and so on.... is there an easy way to install all those packages "all in one"? thanx

---

### Post by givré on 2006-08-15
I guess it's simply because you don't have dapper-update & dapper-security  (or breezy update & breezy-security) for all channel, leading to a no compatibility between some few package.
Post here your /etc/apt/sources.list

---

### Post by the_nomad on 2006-08-17
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse


deb-src [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
# deb-src [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


p.s. i tried install any other program which depends on something and i get the same error.. and all this since ive installed that "universe" and "multiverse" support packages. thanx for helping me!

---

### Post by givré on 2006-08-17
> deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse


You can't really mix breezy & dapper package, on the majority of the case, you will fail on dependency issue, just like the one you have now.
You should remove those line before retrying.

---

### Post by the_nomad on 2006-08-17
i tryed but it seems ive no permisions to do that and neither to modify this thing by going to files properties i cant, these options are disabled :(

---

### Post by givré on 2006-08-17
To change your sources.list, you need to be root. In a terminal, just launch
```
gksu gedit /etc/apt/sources.list
```
remove the 2 dapper line, or comment them, save the file, update
```
sudo apt-get update
```
and that should be ok

---

