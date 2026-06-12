---
title: "Error when installing applications"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by rusty09 on 2008-02-10
I recently downloaded an album and the tracks happen to be in .WMA format, so i was unable to play them. After some searching i found that i would need to install the "restricted extras" program. I tried to install it but i get the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This happens when i try to install any application, i have no idea what it is or how to fix it.  Any help would be appreciated

---

### Post by PmDematagoda on 2008-02-10
Open a terminal and execute:-
```
sudo dpkg --configure -a
```
as suggested by the error, after that is finished your problem should be solved.

---

### Post by spiderbatdad on 2008-02-10
looks like your sources are commented out...if you installed without a working internet connection.
In your terminal run ```
gksu gedit /etc/apt/sources.list
``` and remove the # marks in front of downloadable sources. make it look more like mine.
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2)]/ gutsy main restricted
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

save the file and run:```
sudo apt-get update
```

---

### Post by rusty09 on 2008-02-10
I did the downloadable list thing mentioned above..and now when I  open the add/remove programs, I click on the box to select the app and it just freezes there..

---

### Post by spiderbatdad on 2008-02-10
probably apt is still in use. maybe reboot and run "sudo apt-get update" again...look for any errors. Follow terminal instructions.

---

