---
title: "synaptic fails"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by okkie on 2007-12-14
after a month's trying to get my ati 9250 card working in gutsy i came across  "source-o-matic" from the nl and now can not get into synaptic.sudo synaptic says i must go to synaptic dialog as sources list can not be read.line 237 of sources list must apparently be removed and i don't know how.is there a way to reinstall the original gutsy sources list or how can i clear the rubbish i now have and then reinstall? thanks

---

### Post by taurus on 2007-12-14
Post your /etc/apt/sources.list here then.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

Otherwise, here is my version.

```

#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by okkie on 2007-12-16
thanks taurus.looks like my system will not react unless the following is done okkie@mealone:~$ sudo apt-get update
[sudo] password for okkie:
E: Type 'http://www.ubuntu-nl.org/source-o-matic/' is not known on line 237 in source list /etc/apt/sources.list
okkie@mealone:~$ 

where can i find line 237 and should i just delete it?

i tried this as well 
okkie@mealone:~$ sudo apt-get sources list
E: Invalid operation sources
okkie@mealone:~$ 
can not find my sources list

---

### Post by okkie on 2007-12-16
i should give you this as well 
/etc/apt/sources.list   permission is denied

---

### Post by taurus on 2007-12-16
```
**cat** /etc/apt/sources.list
```

---

### Post by okkie on 2007-12-16
solved thanks. at least i can start somewhere again.

---

