---
title: "Can't UPDATE Ubuntu"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-16
Weird, I was trying to enable, disable, and tried to restart my connection, still the **sudo apt-get update** and **sudo aptitude update** commands does not work!

I think pressing **Ctrl+C** to continue checking for updates, since it hangs, there might be some side effects.

Can you please help me and clarify this? Oh yeah, I am going to post the I think, a bug, where in when you play YouTube Videos, processor goes 100% with system load of more than 3++

SEE the **SCREENSHOTS** ...

[SIZE=1]*To my previous posts, I will reply to it later...*[/SIZE]

---

### Post by overdrank on 2008-02-16
> **karlo said:**
> Weird, I was trying to enable, disable, and tried to restart my connection, still the **sudo apt-get update** and **sudo aptitude update** commands does not work!

I think pressing **Ctrl+C** to continue checking for updates, since it hangs, there might be some side effects.

Can you please help me and clarify this? Oh yeah, I am going to post the I think, a bug, where in when you play YouTube Videos, processor goes 100% with system load of more than 3++

SEE the **SCREENSHOTS** ...

[SIZE=1]*To my previous posts, I will reply to it later...*[/SIZE]

HI and have you tried to change servers? Under system, administration, software sources.

---

### Post by karlo on 2008-02-16
> **overdrank said:**
> HI and have you tried to change servers? Under system, administration, software sources.

I is because of that **one**? Because I used autodetect, and it selected the nearest server to me... Can you test it on your PC too? The **taiwan** server?

---

### Post by jan quark on 2008-02-16
select the main server and train again

pleas post also your sources list file
```

cat /etc/apt/sources.list
```

---

### Post by karlo on 2008-02-17
> **jan quark said:**
> select the main server and train again

pleas post also your sources list file
```

cat /etc/apt/sources.list
```

**sources.list**

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ph.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://www.getautomatix.com/apt gutsy main
deb http://download.tuxfamily.org/syzygy42 gutsy exaile

#AUTOMATIX REPOS START
deb http://security.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse #Added by software-properties
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse #Added by software-properties
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-proposed main restricted universe multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-proposed main restricted universe multiverse #Added by software-properties
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END

deb http://ppa.launchpad.net/stemp/ubuntu gutsy main
deb-src http://ppa.launchpad.net/stemp/ubuntu gutsy main

deb http://ppa.launchpad.net/tualatrix/ubuntu gutsy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu gutsy main
deb http://repository.akirad.net akirad-gutsy main
deb-src http://repository.akirad.net akirad-gutsy main
```

---

