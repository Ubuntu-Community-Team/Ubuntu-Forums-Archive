---
title: "915resolution"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by Bad Apple on 2006-11-25
i have an intel 845gl and have been adviced to install either the 915 or 815resoluion packages to rectify my problems of resolution

trouble is, i have tried the package manager and the command line, but i can not find 915resolution, or the 815 anywhere?!?!?

this is the command i entered
```

sudo apt-get install 915resolution

```

which outputs
```

E: couldn't find package 915resolution

```

---

### Post by taurus on 2006-11-25
Please post your /etc/apt/sources.list here!

```
cat /etc/apt/sources.list
```

---

### Post by Bad Apple on 2006-11-25
```
deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by bodhi.zazen on 2006-11-25
[See here](http://ubuntuforums.org/showpost.php?p=1805204&postcount=11)

---

