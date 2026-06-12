---
title: "Source list?"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-04-19
I updated my source list with the recommended source list that is stickied on the repositories

but when i check my update manager it says that some of the packages are NOT AUTHENTICATED

Should i install them?

---

### Post by Sutekh on 2006-04-19
The sources from this thread - [my recommended breezy sources.list](http://ubuntuforums.org/showthread.php?t=92672)?

There are some sources that probably don't have authentication keys, like the ```
## wine
## deb http://wine.sourceforge.net/apt/ binary/
```repository for example.

I am always told that pacakges from here can't be authenticated.

What packages are you trying to install?

---

### Post by zxcvbnm on 2006-04-19
well i installed it and my source list is now all screwed up....Do you know where i could get the default source list?

---

### Post by Sutekh on 2006-04-19
```

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu breezy universe
# deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

---

