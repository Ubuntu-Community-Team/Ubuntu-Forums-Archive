---
title: "[SOLVED] 'Could not resolve' problem in upgrading"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by drawman on 2007-10-26
I am trying to upgrade to Gutsy from Feisty and get the following:

[http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:) Could not resolve 'wine.lowvoice.nl' 
[http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not resolve 'wine.lowvoice.nl' 
[http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:) Could not resolve 'wine.lowvoice.nl' 

is there any way to remove these troublesome links?

---

### Post by Maestro23 on 2007-10-26
> **drawman said:**
> I am trying to upgrade to Gutsy from Feisty and get the following:

[http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:) Could not resolve 'wine.lowvoice.nl' 
[http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not resolve 'wine.lowvoice.nl' 
[http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:) Could not resolve 'wine.lowvoice.nl' 

is there any way to remove these troublesome links?

Post your /etc/apt/sources.list

> cat /etc/apt/sources.list

You've got a reference to that source in your list that needs to be deleted or commented out.  Probably under a section labeled Automatix.

---

### Post by drawman on 2007-10-26
Is this what you want?


 cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by ricsenior on 2007-10-28
I've just had the same problem.

Run 
    gksu gedit /etc/apt/sources.list

then comment out reference to wine as follows
 #deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

---

### Post by drawman on 2007-10-29
ricsenior & Maestro23:

Thank you for your help.  I have upgraded to 7.10.

---

