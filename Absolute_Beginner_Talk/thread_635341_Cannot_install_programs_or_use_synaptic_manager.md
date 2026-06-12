---
title: "Cannot install programs or use synaptic manager"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by danbar on 2007-12-08
I just wrote a command in the terminal and had a total disaster! I'm having these messages now!

UPDATE MANAGER'S MESSAGE
A unresolvable problem occurred while initializing the package information. 

Please report this bug against the 'update-manager' package and include the following error message: 

'E:Type '--09:02:53--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

ADD REMOVE PROGRAMS' MESSAGE: This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

SYNAPTIC MANAGER'S MESSAGE 
E: Type '--09:02:53--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list 
E: The list of sources could not be read. 
Go to the repository dialog to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by spiderbatdad on 2007-12-08
could you post /etc/apt/sources.list  from your file system?

---

### Post by thelatinist on 2007-12-08
What command did you type?

---

### Post by wjp.reg on 2007-12-08
> **thelatinist said:**
> What command did you type?

```
gksu gedit /etc/apt/sources.list
```

Then copy to your reply

---

### Post by wjp.reg on 2007-12-08
OOPS, wrong guy :confused::lolflag:

But this may help..

---

### Post by danbar on 2007-12-08
Thanks for your wonderful help! I'm doing paste from my file.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator

deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator

---

### Post by danbar on 2007-12-08
The problems were created when I tried to follow this page on the web......
[http://lifehacker.com/software/linux/rip-dvds-in-linux-the-semi+easy-way-330983.php](http://lifehacker.com/software/linux/rip-dvds-in-linux-the-semi+easy-way-330983.php)

---

### Post by danbar on 2007-12-08
The command, if I remember well was.....sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

---

### Post by thelatinist on 2007-12-09
> **danbar said:**
> The problems were created when I tried to follow this page on the web......
[http://lifehacker.com/software/linux/rip-dvds-in-linux-the-semi+easy-way-330983.php](http://lifehacker.com/software/linux/rip-dvds-in-linux-the-semi+easy-way-330983.php)

Maybe I'm confused.  I thought you said in your first post that the problem was created when you typed a command in the terminal.  I'm looking at that page and all I see are graphical utilities...

---

