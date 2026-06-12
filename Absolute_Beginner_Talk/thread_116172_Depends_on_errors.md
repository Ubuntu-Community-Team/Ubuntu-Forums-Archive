---
title: "Depends on errors"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by UnseenMenace on 2006-01-12
Im attempting to install an application which errors with the following comments :-

> 
Depends: kdelibs4 (>=4:3.3.2-6.2) but it is not installable
 Depends: libqt3c102-mt (>=3:3.3.4) but it is not installable

now I have kdelibs 4:3.4.3-Oubuntu1 installed but apt-get does not seem to recognise libqt3c102 and I have not been able to locate it on ubuntu package search.... can anyone help resolve this issue ?

---

### Post by aysiu on 2006-01-13
[QUOTE=UnseenMenace]Im attempting to install an application which errors with the following comments :-

now I have kdelibs 4:3.4.3-Oubuntu1 installed but apt-get does not seem to recognise libqt3c102 and I have not been able to locate it on ubuntu package search.... can anyone help resolve this issue ?[/QUOTE] Can you say the name of the package *and* post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by Kabal on 2006-01-14
Hiya!
I've got the same problem with installing skype on 5.10 Breezy

sudo apt-get install skype will result in:

The following packages have unmet dependencies:
  skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but it is not installable
E: Broken packages

sudo apt-get install libqt3c102-mt
results in:

Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate

My sources.list is follows:

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free


Who can explain? :)
TIA

---

