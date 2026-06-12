---
title: "Something seems wrong with my sources.list(no Deluge in synaptic)"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by offline on 2007-11-01
I think something is wrong with my sources.list(or the 3 keys I have). For example I searched for deluge from synaptic and add-remove programs but it's not there.

My sources.list(feisty):Can you check it?Thanks.

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
```

---

### Post by offline on 2007-11-01
Do we have Deluge in Feisty repositories??

---

### Post by Maestro23 on 2007-11-01
> **offline said:**
> Do we have Deluge in Feisty repositories??

You can get the .deb from their site: [http://deluge-torrent.org/downloads-ubuntu](http://deluge-torrent.org/downloads-ubuntu)

*I know for Gutsy, its in the Universe Repo.

---

