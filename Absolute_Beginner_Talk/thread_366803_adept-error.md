---
title: "adept-error"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Xvani on 2007-02-21
Hi!

When I attempt to open Adept packet manager I get the following error:

"could not open cache - adept manager
the apt database could not be opened! this may be caused by incorrect apt configuration or some similar problem. try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem"

I have tried apt-get update (and upgrade for that matter), and get the following error:
E: Type 'http://archive.ubuntu.com/ubuntu' is not known on line 1 in source list /etc/apt/sources.list

I have tried apt-setup (also with sudo) and I get:
Command not foumd

What to do?

---

### Post by Xvani on 2007-02-21
Here is a print of my sources.list file:
```

http://archive.ubuntu.com/ubuntu


# deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted 

deb http://no.archive.ubuntu.com/ubuntu/ edgy main restricted 
deb-src http://no.archive.ubuntu.com/ubuntu/ edgy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu/ edgy-updates main restricted 
deb-src http://no.archive.ubuntu.com/ubuntu/ edgy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://no.archive.ubuntu.com/ubuntu/ edgy universe 
deb-src http://no.archive.ubuntu.com/ubuntu/ edgy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 
deb-src http://no.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu edgy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted 
deb http://security.ubuntu.com/ubuntu edgy-security universe 
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

---

### Post by lossennarion on 2007-02-21
Solved. Had to remove the first line

---

