---
title: "Cant install programs"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by SomeRandomGuy63 on 2008-01-27
So ive just installed ubuntu and am ,loving it but i cant install any programs. i cant use the terminal that alwatys says "package not found". when i try and install a .deb pacakge (one which is meant to work in ubuntu) it gives me an error. if i try and uise add/remove it says i need a working internet connection which i have. Im not sure what the problem is it seems like firefox is the only thing that can acseess the internet. 

heres what generated in the terminal when i execute : cat /etc/apt/sources.list

```
adrian@adrian-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

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

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://packages.dfreer.org gutsy main
deb http://packages.dfreer.org gutsy main
adrian@adrian-desktop:~$ 


```

---

### Post by Ub1476 on 2008-01-27
Almost every repo is has a # in front of it which means it is not in use. Open System|Administration|Software Sources to enable more.

---

### Post by mzembe on 2008-01-27
> **Ub1476 said:**
> Almost every repo is has a # in front of it which means it is not in use. Open System|Administration|Software Sources to enable more.

Gnome?For kde, open your System->AdeptManager and manage your repositories from the 'Adept' tab.

---

### Post by SomeRandomGuy63 on 2008-01-27
im using Ubuntu Gutsy Gibbon.

when you said enable more do you mean these?

[img]http://img99.imageshack.us/img99/925/help1vh2.png[/img]

because that still osent work i get the same message saying i need an internet connection. but now it says "downloading package information" and just hangs but it isnt downloading anything because the data rate is unknow and it has skipped the first files.

when i cancel that it says could not download all repositary indexes and gives me a lis of repo's

---

### Post by RebounD11 on 2008-01-27
Go to the third party softare tab and enable those too (this might be dangerous for updates but so far nothing happened to my installation).

If that doesn't work go and erase the # in front of every line that starts with deb or deb-src in your sources.list.

After doing either one or all of the above ... run sudo apt-get update.

---

### Post by Kevbert on 2008-01-27
Hi. It looks like you're on the right track.  In the 'Download from' box select 'Other' and then try clicking on 'Select Best Server'.

---

### Post by bumanie on 2008-01-27
What you have done is some of the repo's. Go here and do the manual update of repo's, it should give you all the ones you need.
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories)

---

### Post by SomeRandomGuy63 on 2008-01-27
thanks, i managed to fix it. Only problem is when i try to download something that hasent been authenticated i click ok but it shows the download bar but never starts downloading.

nOw i can add new repos and the files show up but again of i try and download something it will goto about 10% then just hang

thanks for all the help so far :)

---

