---
title: "[SOLVED] help source list could not be read"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by peggsydaly on 2007-08-17
i have made a big mistake and i cannot open synaptic package manager anymore. i was pasting install script into terminal when i received this message at the terminal. E: Type  'echo' is not known on line 66 in source list /etc/apt/source.list E: the list of sources could not be read go to the repository dialogue to correct the problem E: _ cache->open() failed, please report.
i don't know where to find the repository dialogue, i don't know what echo is, but i went to my automatix installer and clicked on show source list.  below is what it looks like. i don't think any changes can be made from the automatix displays. can anyone help?:(

# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by overdrank on 2007-08-17
HI use this command and edit you list, in the terminal
```
gksudo gedit /etc/apt/sources.list
```
If you have recently edit that list an d added repos the remove the ones you added. The error id stating that line 66 is the problem.

---

### Post by AlexenderReez on 2007-08-17
> **peggsydaly said:**
> 
#AUTOMATIX REPOS END
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
[B]echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo [/B]apt-get update


delete that or cut then paste to terminal using mouse..you should enter that in terminal...not there....

---

### Post by bodhi.zazen on 2007-08-17
The last two lines are wrong :

> echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Remove them. They are commands to be entered into your terminal.

If you need help with automatix please submit questions to their forums.

---

### Post by r4ik on 2007-08-17
See,

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

As an alternative.

Good luck !

---

