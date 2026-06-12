---
title: "Some included software isn't being installed"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Justus on 2005-12-07
Quite a bit of the software (that I thought Ubuntu comes with, maybe it doesn't after all) isn't being installed when I install Ubuntu: AbiWord, lots of programming tools, some other browsers/email clients, etc...when go to Add Programs, it says it's not in my archive or something, and that my hardware probably doesn't support them:???: I've installed it on two different computers (a Dell Dimension 3000, and some off brand computer) with the same result. How do I get these programs? Thanks

---

### Post by aysiu on 2005-12-07
Open a terminal (Applications > Accessories > Terminal) and type in these commands. Then, post the output of these commands into a post here. ```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get install abiword
```

---

### Post by Justus on 2005-12-07
```
justus@Justus:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe




justus@Justus:~$ sudo apt-get update
Reading package lists... Done



justus@Justus:~$ sudo apt-get install abiword
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package abiword
```

Haven't been able to connect to a dial-up connection yet though, so that's why apt-get isn't working...still trying to figure that out. Getting frustrating](*,)

---

### Post by aysiu on 2005-12-07
Do you realize your only source is the Breezy installer CD? I'm not sure Abiword is on that...

**Edit**: Yeah, I double-checked the CD-ROM--AbiWord isn't on it.

---

### Post by Justus on 2005-12-08
Alright, thanks lol...I'll just have to keep trying to get that internet working *sigh*

---

