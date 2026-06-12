---
title: "Is adding unsupported feisty updates(backports) dangerous?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by offline on 2007-11-02
I don't have any main backports repositories enabled but recently I enabled unsupported feisty updates(backports)  and immediately there were updates to gnucash, gnupg etc

Can this updates be somehow dangerous for the stability of my feisty or would present a danger whenever I upgraded to 7.10?

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty restricted main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-security restricted main
deb http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-updates multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe

```

---

### Post by SOULRiDER on 2007-11-02
IMHO and my experience i say not at all.

---

