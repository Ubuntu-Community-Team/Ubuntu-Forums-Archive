---
title: "[SOLVED] Problem with synaptic"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Charlie11x on 2008-01-20
I am running Kubuntu 7.10 and I tired to add the respiratories to install wine.
When I went to open synaptic, i got this error

```
E: Type 'sudo' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```

Please help me, as i can't even install anything via terminal either.

---

### Post by forestpixie on 2008-01-20
post the output of this from terminal

cat /etc/apt/sources.list

---

### Post by Charlie11x on 2008-01-20
```
deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
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
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

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
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.listsudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.listhttp://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```

---

### Post by forestpixie on 2008-01-20
open the file to edit 

```
gksudo gedit /etc/apt/sources.list
```

delete the last line, that should have been run in terminal I think

save, close and run 

```
sudo apt-get update
```

then try and do whatever you were doing again

---

### Post by Charlie11x on 2008-01-20
When I try the first line you gave me, i get this
```
The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksudo: command not found
```
so i try and run the line it gave me sudo apt-get install gksu, it asks for my password, and i get this
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
Thnx for your help so far by the way.

---

### Post by forestpixie on 2008-01-20
are you not running ubuntu then - if you're using kubuntu replace 

gksudo gedit with kdesu kate 

at some point - it might be worth changing your profile and adding the os you're using

---

### Post by Charlie11x on 2008-01-20
Thank you so much, that solved my problem.
And I will be sure to change my profile to Kubuntu or whatever.
If I knew how to give you a thank you on your profile, I would.

---

### Post by forestpixie on 2008-01-20
glad I could help - you can click the little star/ribbon thing to thank people

and I see you've added kubuntu 

and I didn't have to say 'can you mark thread solved' either

:lol:

---

