---
title: "Unable to install open-iscsi package"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by trini0 on 2007-10-21
Hello all
Im curenlty running Edgy Eft (6.10), and I'm trying to install the open-iscsi package.
From what I can tell, a package exists for open-iscsi
[http://packages.ubuntu.com/feisty/net/open-iscsi](http://packages.ubuntu.com/feisty/net/open-iscsi)

Here is my /etc/apt/sources.list file
```

#
# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release amd64 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release amd64 (20061025.1)]/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse 
```

I performed an apt-get update, then I try to install but it complains that it cannot find open-iscsi

xx@xxx:/etc/apt$ sudo apt-get install open-iscsi
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package open-iscsi

Any pointers would be greatly appreciated.
Thanks

---

### Post by schorsch on 2007-10-21
The package "open-iscsi" is not available in Edgy but in Feisty, Gutsy and Hardy. So either update fo Feisty or try to build the package from the sources.

---

### Post by trini0 on 2007-10-21
Thanks for the fast reply

---

