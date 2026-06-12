---
title: "package install errors"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by uknowho008 on 2007-11-09
i keep getting errors when i install things. for instance today i installed the internet sync time thing and i got an error.

i tried to copy the error but i guess it didnt work. it was something like syscups or something like that. whats going on? it might have started after installing automatix2.

---

### Post by Maestro23 on 2007-11-09
> **uknowho008 said:**
> i keep getting errors when i install things. for instance today i installed the internet sync time thing and i got an error.

i tried to copy the error but i guess it didnt work. it was something like syscups or something like that. whats going on? it might have started after installing **automatix2**.

Magic words.  Works for some and I have read horror stories from others. Anyway...

Can you post your **/etc/apt/sources.list**

In a terminal:

> cat /etc/apt/sources.list

Copy/Paste here.

---

### Post by uknowho008 on 2007-11-09
here you go

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

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse




## Custom
# deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) etch main non-free contrib
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

## MoBlock
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
#AUTOMATIX REPOS END


Thanks for the help

---

### Post by uknowho008 on 2007-11-09
i think i commented out the debian one because i was getting other errors from it too...

---

### Post by Maestro23 on 2007-11-09
> **uknowho008 said:**
> i think i commented out the debian one because i was getting other errors from it too...

List looks good as far as the Ubuntu repositories.  So, you get errors on anything you try to install?

---

### Post by uknowho008 on 2007-11-09
yep anything i try to install or update. should i jut get rid of automatix? it doesnt even really seem like there is anything that i cant get from the normal ubuntu package manager. at least it seems like ive seen most everything in both.... i got codecs just by having it search for me when i tried to play something in the past and thats the only thing i think i never saw in the package manager.

---

### Post by uknowho008 on 2007-11-09
i just uninstalled automatix2 and then installed a couple programs and im still getting the same error. the programs seem to work fine though...

E: cupsys: subprocess post-installation script returned error exit status 1
E: ntp: subprocess post-installation script returned error exit status 1

---

