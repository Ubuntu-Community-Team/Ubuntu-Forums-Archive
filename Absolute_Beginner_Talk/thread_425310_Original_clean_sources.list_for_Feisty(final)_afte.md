---
title: "Original clean sources.list for Feisty(final) after a clean install"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by whee on 2007-04-27
Could anyone post the original clean /etc/apt/sources.list for Feisty(final) after a clean install.(no custom repositories, just the original one you get after a clean Feisty(final) install.
I messed a bit with mine, but forgot to make a backup.
A URL from an official Ubuntu resource would also suffice.

---

### Post by Seisen on 2007-04-27
Post your source list maybe we can fix for you.

---

### Post by BHelts on 2007-04-27
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

---

### Post by zvacet on 2007-04-27
[http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/")

---

### Post by whee on 2007-04-27
@Bhelts
Thanks, that did the trick :)

@Seisen
Initially i added a whole bunch of repositories to mine, but later decided to delete a whole bunch again, but i felt i was left with less repositories at the end than the original one, but i copied Bhelts reply and all seems ok now. Thanks.

@zvacet
Thanks

---

