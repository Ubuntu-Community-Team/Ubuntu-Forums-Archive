---
title: "NTFS write access"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by RandomBob on 2006-11-20
I'm running Ubuntu 6.06
I've got two NTFS partitions /dev/hda5 and /dev/hdb1
How do I enable full read/write access for all users?
I've tried sudo apt-get install ntfs-3g
it reports :
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-3g

Arg! What do I do?? why is this so hard?!

Thanks

---

### Post by Zaffe on 2006-11-20
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by kosmic on 2006-11-20
To install ntfs-3g you need to have the "Universe" repo active in your sources.list.

ex.: sudo gedit /etc/apt/sources.lst

then enable Universe, or go to "synaptic", Configuration -> Repositories -> and enable Universe

---

### Post by RandomBob on 2006-11-20
I think I've done that. Heres a copy of my /etc/apt/sources.list

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted

---

### Post by 56phil on 2006-11-20
I'd suggest that you backup your NTFS volumes frequently. That write to NTFS software is very new.

---

### Post by delphiguy on 2006-11-20
yeah ntfs-3g rocks... great tool for people like me who is migrating from windows into linux.  I used for about 2 months until I got a new harddisk and was ready to format my ntfs partition to ext3.

---

