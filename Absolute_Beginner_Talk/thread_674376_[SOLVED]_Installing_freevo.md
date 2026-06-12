---
title: "[SOLVED] Installing freevo?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2008-01-21
How do you install freevo? i kinda followed the intructions on there site for gutsy but with my little understanding it didn't work so can someone explain how to do it? sorry if this sounds like a stupid question...

---

### Post by Arthur Archnix on 2008-01-21
Got a link to the instructions you've tried? Also, what errors (messages?) did you encounter?

---

### Post by kamitsukai on 2008-01-21
[http://doc.freevo.org/FreevoAptUbuntu](http://doc.freevo.org/FreevoAptUbuntu) to add the software sources i went to system->Administration->software sources and then i did everything else in the terminal...

---

### Post by Arthur Archnix on 2008-01-21
Post the output of ```
cat /etc/apt/sources.list
```

---

### Post by kamitsukai on 2008-01-21
```
carl@Carls-Pc:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

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
deb http://ubuntu.geole.info/ gutsy universe multiverse
deb-src http://ubuntu.geole.info/ gutsy universe multiverse
carl@Carls-Pc:~$ 

```

---

### Post by Arthur Archnix on 2008-01-21
Ok, now do this: ```
sudo apt-get update && sudo apt-get install geole-keyring
```

---

### Post by kamitsukai on 2008-01-21
OK done that...but what did _that_ do? :)

---

### Post by Arthur Archnix on 2008-01-21
Hmm.... I think they're bad instructions. Try:
```
sudo apt-get install freevo
```
If that doesn't work, post the output of:
```
sudo apt-cache search freevo*
```

---

### Post by kamitsukai on 2008-01-21
it wants to know video output?

---

### Post by Arthur Archnix on 2008-01-21
I dunno man. I just came here to help you get it installed. I'd say go with X11. You can always change it later using the config files. [http://doc.freevo.org/Configuration](http://doc.freevo.org/Configuration)

Cool looking desktop by the way. 8-)

EDIT: Oh, and you should just capture the active window. Personal information can sometimes get caught in the screencap. Like the name in the top panel.

---

### Post by kamitsukai on 2008-01-21
lol thanks :P

---

