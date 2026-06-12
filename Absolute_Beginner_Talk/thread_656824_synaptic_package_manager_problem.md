---
title: "synaptic package manager problem"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by rutilajw on 2008-01-03
E: The package mplayer-386 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Yea, I get that error (or close to it) when I open synaptic packet manager, add/remove programs, and update manager.  Oh, and also when I install from command line.

I don't know what to do

---

### Post by Xavieran on 2008-01-03
try sudo dpkg --configure -a
That fixed an error similar to this for me...

---

### Post by rutilajw on 2008-01-03
Same thing still happens.

---

### Post by sciencewhiz on 2008-01-03
can you post your /etc/apt/sources.list

```
cat /etc/apt/sources.list
```

---

### Post by rutilajw on 2008-01-03
jacob@jacob-laptop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by carrett on 2008-01-03
There is no mplayer-386 (at least not on packages.u.c). I'd recommend removing it (apt-get remove mplayer-386) and then installing the mplayer package (apt-get install mplayer) which IS in the archives for sure.

Good luck.

---

### Post by forestpixie on 2008-01-03
try this

```
sudo apt-get install -f
```

---

### Post by rutilajw on 2008-01-03
jacob@jacob-laptop:~$ sudo apt-get remove mplayer-386
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mplayer-386 needs to be reinstalled, but I can't find an archive for it.
jacob@jacob-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mplayer-386 needs to be reinstalled, but I can't find an archive for it.
jacob@jacob-laptop:~$ 


those are the two commands you guys gave me.

seems nothing is working

---

