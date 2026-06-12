---
title: "processing errors"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by yimmmy on 2008-02-12
hi 
heres whats going on,
ive just upgraded my ubunut to ubuntu gusty threw the auto updater after i updated i had some trouble with the themes and what not but i fixed that . i was trying to install some programs such as firefox and little things but every time i tryed to install them i ve gotten an error  ```
dpkg: error processing gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-terminal-data
 gnome-terminal
 gnome-core
 gnome-screensaver
 gnome-desktop-environment
 planner
 gnome-office
 gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
i was trying to install some system critical items but i couldnt i got the followed error
help would be nice:)

---

### Post by spiderbatdad on 2008-02-12
seems like sources are not up to snuff.  Here's a copy of my sources.list, if you like. Maybe you could use it as yours and update from it.
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by yimmmy on 2008-02-12
K 
i put it in there and it all updated fine so im going to try installing some stuff! thanks
one thing 
i seen that your source list was for the beta will that hurt any thing?

---

### Post by spiderbatdad on 2008-02-12
That's just the cd I used...The sources are good....Canonical is there....and I can't remember the mirror...it was a major university. But the sources are Gutsy main.

---

### Post by yimmmy on 2008-02-12
well the upgrade went fine but when i tryed to install something it gave me the error again ```
E: gnome-terminal-data: subprocess post-installation script returned error exit status 1
E: gnome-terminal: dependency problems - leaving unconfigured
E: gnome-core: dependency problems - leaving unconfigured
E: gnome-screensaver: subprocess post-installation script returned error exit status 2
E: gnome-desktop-environment: dependency problems - leaving unconfigured
E: planner: subprocess post-installation script returned error exit status 2
E: gnome-office: dependency problems - leaving unconfigured
E: gnome: dependency problems - leaving unconfigured


```
ive installed all the gnome apps and data stuff i really dont know what s wrong!!

---

### Post by spiderbatdad on 2008-02-12
sorry I don't know more about upgrading the way you did. I have run sudo apt-get dist-upgrade before, but generally, I save everything I want to cd's, then start with a clean install of the latest release.

---

### Post by yimmmy on 2008-02-12
yea i tryed that it kept giving me a bad cd error in two drives , it was the cd frm ubunt as well im going to try to install a diff v. of ubuntu say ubuntu studios

---

