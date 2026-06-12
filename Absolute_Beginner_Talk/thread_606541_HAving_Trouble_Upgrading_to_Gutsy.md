---
title: "HAving Trouble Upgrading to Gutsy"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Vuto on 2007-11-08
when I try and upgrade from feist to gutsy I keep getting this error
```
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg Could not resolve 'wine.lowvoice.nl'
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_AU.bz2 Could not resolve 'wine.lowvoice.nl'
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz Could not resolve 'wine.lowvoice.nl'

```
And then I click close and it does not continue the upgrade

Anyone know why? or more importantly a solution to this problem

Thnx

---

### Post by Maestro23 on 2007-11-08
> **Vuto said:**
> when I try and upgrade from feist to gutsy I keep getting this error
```
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg Could not resolve 'wine.lowvoice.nl'
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_AU.bz2 Could not resolve 'wine.lowvoice.nl'
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz Could not resolve 'wine.lowvoice.nl'

```
And then I click close and it does not continue the upgrade

Anyone know why? or more importantly a solution to this problem

Thnx

Post your /etc/apt/sources.list

> cat /etc/apt/sources.list

*Need to delete the entries for that source.

---

### Post by Vuto on 2007-11-09
This is what came up
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted multiverse
#AUTOMATIX REPOS END

So any idea on whats going wrong?

---

### Post by rsambuca on 2007-11-09
I would seriously backup your data before upgrading.  It is likely that it won't go very smoothly since you have been using all of those outside repositories.  You need to put a '#' in front of all of the lines between the #AUTOMATIX lines.

---

### Post by RayneStorm on 2007-11-11
I have the same exact problem while trying to upgrade to gusty.  How do I remedy that problem?

---

### Post by crf on 2007-11-11
> **RayneStorm said:**
> I have the same exact problem while trying to upgrade to gusty.  How do I remedy that problem?

Did you try what rsambuca suggested: "You need to put a '#' in front of all of the lines between the #AUTOMATIX line"?

--
Try also going to add/remove applications from the Applications menu, choosing preferences, and then in the third party software tab, uncheck the appropriate boxes next to urls that were in the error messages.

---

### Post by RayneStorm on 2007-11-14
How do I add # to the source list entries?

Nevermind, I figured it out... I'm gonna try and install again, I'll report back if I have any problems.

Thanks for the help!

---

### Post by cfrivas on 2007-11-17
Reply to crf:
I Try also going to add/remove applications from the Applications menu, choosing preferences, and then in the third party software tab, uncheck the appropriate boxes next to urls that were in the error messages. Now am in the middle of upgrade to 7.10.
Now "Support for some applications have ended":
binfmt-support
fiesty-session-splashes
gcj-4.1-base
gij-4.1
gnome-cups-manager
libgda2-3
libgda2-common
libglib1.2
li9bgnomecupsui1.0-1c2a
libgtk1.2
libgtk1.2-common
libilzo1
libpcap0.7
libportaudio0
libslab0
libstlport5.1
openoffice.org-filter-mobiledev
ttf-baekmuk
vnc-common
xarchiver
xvncviewer
"Connical Ltd. no longer provides support for the following software packages. You can still get support from the community.
If you have not enables community maintained software (universe), these packages will be suggested for removal at end of the upgrade"

---

### Post by Vuto on 2007-11-22
sorry to be naive but I still have no idea how to upgrade, what do I do now?

---

### Post by Vuto on 2007-11-22
bump

---

