---
title: "Download Update: Not Authenticated?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by e30ernest on 2007-12-23
I have that update star on my taskbar and when I click it I get that the updates listed can not be authenticated.  The files are:

```
findutils
mysql-common
libmysqlclient15off
```

Did any of you get this problem?  Is it safe to update?  I am using Gutsy.  Thanks!

---

### Post by hyper_ch on 2007-12-23
please post your /etc/apt/sources.list

---

### Post by e30ernest on 2007-12-23
Doh forgot!  Here you go:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ph.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://repo.freecreations.info/ubuntu gutsy freeverse

```

---

### Post by hyper_ch on 2007-12-23
if you are sure this is a reliable repo then everything is ok:

deb [http://repo.freecreations.info/ubuntu](http://repo.freecreations.info/ubuntu) gutsy freeverse

---

### Post by e30ernest on 2007-12-24
I got it from this thread when I installed AWN:

[http://ubuntuforums.org/showthread.php?t=581620&highlight=http%3A%2F%2Frepo.freecreations.info%2Fubuntu](http://ubuntuforums.org/showthread.php?t=581620&highlight=http%3A%2F%2Frepo.freecreations.info%2Fubuntu)

I'm still unsure if I should update or just remove the questionable source from the list.

---

### Post by hyper_ch on 2007-12-24
That message mean that you did not apply a correct GPG key for that repository. It's just one level of protection. E.g. another key can result by having taked that side over by a malicious third party... then you would have a key mismatch.
But then I tend to think you probably didn't get the correct key first-place.

---

