---
title: "mythexport missing from deb?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Dontgetit on 2008-03-04
Hello... i'm trying to install mythexport per the wiki... but it's telling me the package can't be found... can anyone please help me to find it?

---

### Post by glennric on 2008-03-04
From a google search it appears that this is a package in Hardy.  It does not appear to be available in Gutsy.

---

### Post by taurus on 2008-03-04
Which wiki and have you looked in your /etc/apt/sources.list to make sure you have enable all the repos?

Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by jan quark on 2008-03-04
[http://packages.ubuntu.com/hardy/mythexport](http://packages.ubuntu.com/hardy/mythexport)

---

### Post by Dontgetit on 2008-03-04
This is the wiki where it seems to be avail for gutsy:
[https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)


And this is the list of sources on my sys:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) gutsy main

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://ppa.launchpad.net/rhpot1991/ubuntu](http://ppa.launchpad.net/rhpot1991/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/rhpot1991/ubuntu](http://ppa.launchpad.net/rhpot1991/ubuntu) hardy main

---

### Post by jan quark on 2008-03-04
**_ouch_**

[B]please delete automatix from your system
it is known to cause heavy compatibility issues[/B]

---

### Post by Dontgetit on 2008-03-04
10-4... i think my brother put it on there...

Do you think that's why mythexport is not showing up?  Thank you for your help.

---

### Post by jan quark on 2008-03-04
do not know 

did you install something with automatix?

---

### Post by Dontgetit on 2008-03-04
Nope.  Are you able to download a pkg from the debs listed on the wiki in gutsy?  It's like they're not there...

---

### Post by Dontgetit on 2008-03-04
Bump (please?)

---

### Post by rhpot1991 on 2008-03-31
Did you ever get this working?  For Gutsy you need to add my PPA to your /etc/apt/sources.list as it says in the wiki.  The package is only officially included into Ubuntu on Hardy.

---

