---
title: "Problem starting Synaptics"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by mohanr on 2007-08-23
Good Evening all,

Am running Dapper and am having problems using Synaptics. I get the following error

E: Read error - read (22 Invalid argument)

I get a similar error when running apt-get install  from the terminal line

Reading package lists... Done
E: Read error - read (22 Invalid argument)

I am able to run apt-get update but not install or remove.

I see that the /etc/apt/sources.list is populated and error free. Any idea what the problem could be?

Thanks, 
Mohan

---

### Post by wormser on 2007-08-23
It looks similar to other errors I have seen with the sources.list file.  Post your /etc/apt/sources.list for us to look at.

---

### Post by mohanr on 2007-08-23
**Thanks for the reply - Here it is**
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
#deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
## deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main multiverse
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu) dapper universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

---

### Post by alienexplorers on 2007-08-23
Try typing in TERMINAL
> sudo aptitude update

---

