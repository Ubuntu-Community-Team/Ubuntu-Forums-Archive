---
title: "Add/Remove does not work."
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by xItachi on 2007-12-03
Hi, when I try to install things with Add/Remove.. it finds the programs but when I check the box to mark it for installation, it says "the list of applications is unavailable" and it just prompts me to reload the page, taking me back to square one.  This also happens when I try to play *.mp3's and it finds the plugins but cannot install them because "the list of applications is unavailable."  I have just recently installed Ubuntu 7.10, but during the installation I remember that it did not complete the security updates because I wasn't connected to the internet.  Perhaps that is the reason?  I also have many problems/things missing when I try to install things by cd'ing into the folder and using the './configure' and 'make' commands, such as no gcc compiler or anything of the sort, makefile not found,.. etc.  Thank you very much for all your help.

---

### Post by PmDematagoda on 2007-12-03
Please post the result of:-

```
cat /etc/apt/sources.list
```

---

### Post by xItachi on 2007-12-03
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

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

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by PmDematagoda on 2007-12-03
Open your sources.list file for editing using:-
```

sudo gedit /etc/apt/sources.list
```

Then remove the # in front of all the repository addresses, for example, these:- 

```
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
```

Should look like this:-

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
```

After the editing is done, do:-

```
sudo apt-get update
```

Then try using Add/Remove again.

---

### Post by xItachi on 2007-12-03
Thanks a lot PmDematagoda, this worked out great!

---

