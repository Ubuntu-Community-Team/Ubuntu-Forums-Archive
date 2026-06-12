---
title: "Upgrading to 7.10"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Ionamay on 2007-10-18
When I try to upgrade it goes quite far then says-

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve ‘wine.lowvoice.nl’
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_GB.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_GB.bz2) Could not resolve ‘wine.lowvoice.nl’
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve ‘wine.lowvoice.nl’

and then cancels the upgrade. Please help :P

---

### Post by celticbhoy on 2007-10-18
Have you unchecked all repo's other than official Ubuntu one's

---

### Post by FredB on 2007-10-18
> **Ionamay said:**
> When I try to upgrade it goes quite far then says-

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve ‘wine.lowvoice.nl’
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_GB.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_GB.bz2) Could not resolve ‘wine.lowvoice.nl’
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve ‘wine.lowvoice.nl’

and then cancels the upgrade. Please help :P

Comment these lines. There are not official repositories.

---

### Post by LowSky on 2007-10-18
also gutsy is using the newest version of wine

---

### Post by Repent on 2007-10-18
I have pretty much the same problem how can it be fixed? Oh I don't have wine installed.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

Someone please help us!

---

### Post by Ionamay on 2007-10-18
:P I actually have no idea what most of the people are on about here xDD I'm a complete newbie. I need it explained without jargon :P

---

### Post by overdrank on 2007-10-18
> **Ionamay said:**
> :P I actually have no idea what most of the people are on about here xDD I'm a complete newbie. I need it explained without jargon :P

HI you can use this command in the terminal ```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of those sources that will comment them out. Good luck!

---

### Post by bengoza on 2007-10-19
> **overdrank said:**
> HI you can use this command in the terminal ```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of those sources that will comment them out. Good luck!

Hi, I'm having the same problem, and here is the output from the command above:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt feisty main

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
```

Maybe it's Automatix that's messing me up?

---

### Post by sgalland on 2007-10-19
I would try uninstalling your current version of Automatix and remove the repos (not sure if Automatix removes those when uninstalled) and install the Gutsy Automatix.

---

### Post by jinxed on 2007-10-19
Commenting out the repositories is one answer. ...one that I would not recommend. Since your error is really a 404 error (Resource not found), a better approach might be to find a Wine repository that works.

I had the same error, and solved it by changing the wine.lowvoice.nl reference to wine.budgetdedicated.com. You can do this by either directly editing your sources or by going to System -> Administration -> Software Sources. Go to the 'Third party' tab and edit the lowvoice entries.

Easy schmeazy!

---

