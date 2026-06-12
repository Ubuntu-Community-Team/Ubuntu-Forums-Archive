---
title: "avant dock problems"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by hayatago on 2007-12-10
Hi everyone, I'm new to linux, ubuntu is my first one. Problem started after i installed avant dock, my software updates and synaptics cause the following error : 

E: Type '“deb' is not known on line 71 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


anyone know how to resolve this issue.  Help will be much appreciated.  :?

---

### Post by overdrank on 2007-12-10
> **hayatago said:**
> Hi everyone, I'm new to linux, ubuntu is my first one. Problem started after i installed avant dock, my software updates and synaptics cause the following error : 

E: Type '“deb' is not known on line 71 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


anyone know how to resolve this issue.  Help will be much appreciated.  :?

Hi and welcome, you can use this command ```
gksudo gedit /etc/apt/sources.list
``` using the alt, F2 keys and correct line 71 of that list.

---

### Post by hayatago on 2007-12-26
after i inserted gksudo gedit /etc/apt/sources.list, i get the sources list, but what should i do to line 71? should i delete the all the line after 71?

---

### Post by overdrank on 2007-12-26
> **hayatago said:**
> after i inserted gksudo gedit /etc/apt/sources.list, i get the sources list, but what should i do to line 71? should i delete the all the line after 71?

HI and if you could post the output of the command maybe we can help

---

### Post by hayatago on 2008-01-09
Hi after entering gksudo gedit /etc/apt/sources.list this is what is written; 


deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

#Ubuntu Muslim Edition
deb [http://www.ubuntume.com/repository](http://www.ubuntume.com/repository) gutsy main #Ubuntu Muslim Edition
#siahe.com
deb [http://siahe.com/zekr/apt](http://siahe.com/zekr/apt) gutsy main #siahe.com

deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator

deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator

“deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets”
“deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets”
“deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets”
“deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets”
“deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets”
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets

---

### Post by shareMenaPeace on 2008-01-09
Hi, you might want to delete all the screenlets except for the last.line (bottom lines) oh moment

---

### Post by shareMenaPeace on 2008-01-09
Make the last lines (those with screenlet sinit) look like this

> #deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets

If you later get problems with screenlets try removing the "#" , this marks the line  in sources.list to be not run from ubuntu.

---

### Post by shareMenaPeace on 2008-01-09
Did my post helped you, can you proceed now?

---

