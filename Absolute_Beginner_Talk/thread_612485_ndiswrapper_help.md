---
title: "ndiswrapper help"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by tibby_ on 2007-11-13
so i had to use a different computer to downlodad the .inf file and .sys file for my laptop that is running a broadcom bcm4318 wireless card and was wondering how i use the ndiswrapper if all 3 of these items are just sitting on my desktop, cause i have seen quite a few posts about how to do it, but none of them worked for me and was wondering if this had anything to do with it. help would be greatly greatly appreciated. P.S. complete newbie to all of this so slow detailed steps would be amazing ;)

---

### Post by poudin on 2007-11-13
[http://www.linlap.com/wiki/Configuring+the+ndiswrapper+driver+for+wireless+controllers+without+native+Linux+drivers](http://www.linlap.com/wiki/Configuring+the+ndiswrapper+driver+for+wireless+controllers+without+native+Linux+drivers)

ndiswrapper -i <location_of_your_driver>/<the_driver>.inf
ndiswrapper -l

use lspci to confirm your network adaptor and then use the above commands to insert the .inf

check the URL for help...worked for me on a HP DV1000 with no linux drivers for wifi adaptor

---

### Post by tibby_ on 2007-11-14
okay so on the website it says for ubuntu all you do is type in that little code. is that all i have to do? what do i do next?

---

### Post by tibby_ on 2007-11-14
so i put in:
sudo apt-get install ndiswrapper-common 
and put in my password and then it says :
reading package lists... done
building dependncy tree
reading state information... done
E: couldn't find package ndiswrapper-common

---

### Post by poudin on 2007-11-14
post the output of

cat /etc/apt/sources.list

one of the members will be able to tell you which repository you are missing. that is what the ndiswrapper can't be downloaded.

---

### Post by tibby_ on 2007-11-14
here is the output for the line you told me to put in. thanks for all the help so far!!! :)

phattyc@ubuntu:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015)]/ gutsy main multiverse restricted universe

deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015)]/ gutsy main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by poudin on 2007-11-14
k...u can try this...make a backup of your existing sources.list

sudo cp /etc/apt/sources.list /etc/apt/sources.list.original

and the add these repos to your /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted

then you should apt-get update and try getting ndiswrapper again.

I compared vs my /etc/apt/sources.list..and these were the differences.

---

