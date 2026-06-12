---
title: "add/remove apps ERROR"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-20
I got this error while going to the add remove apps menu

```
Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.
```

then I get this error in the terminial.

```
ben@ben-ubuntu:~$ sudo apt-get update
Password:
E: Malformed line 6 in source list /etc/apt/sources.list (dist parse)
ben@ben-ubuntu:~$ 
```

how do i fix it. Is there some kind of system restore i can do or do i have to edit it manually. I have no clu. I hope someone knows.

---

### Post by ProjectWhat on 2007-03-20
this is the sources.list
```
# 
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted #Added by software-properties


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security restricted main multiverse #Added by software-properties
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```

---

### Post by ProjectWhat on 2007-03-20
problem solved: I had to go into the sources menu in the admin menu and take out the cd check marks.

---

### Post by zvacet on 2007-03-20
Is this how you want your sources list to look?It is nothing wrong,but you don´t have universe,backports and edgy-security universe.

---

