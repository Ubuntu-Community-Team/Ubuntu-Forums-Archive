---
title: "error updating"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by personal-data-removed on 2008-04-19
I have Ubuntu herdy heron.

I have 429 possible actulaizations.
When i try to update on "update manager" it says its not possible to do all updates, and asks for me to do a parcial actualization.

I chose parcial actualization, and it gives an error:

Its not possible to autenticate some packages.
avant-window-navigator-bzr
awn-core-applets-bzr
awn-manager-bzr
libawn-bzr
python-libawn-bzr

and updates nothing.

How to solve this and update my system ?

---

### Post by bumanie on 2008-04-19
It is likely awn is not enabled properly re repositories etc. Look [here]("http://wiki.awn-project.org/DistributionGuides") to configure properly. Hope this helps. It is integrated better in hardy

---

### Post by personal-data-removed on 2008-04-19
@bumanie

Thanks for reply.

For Heron, it onlys says this:

Hardy Heron (8.0x) and later
As of version 0.2.1, Awn has been accepted as a package in universe/gnome.
It can be installed by simply running the following in the terminal:
sudo apt-get install avant-window-navigator

I already AWN have installed and running.

Cant find instructions for unblock the 429 updates.

---

### Post by bumanie on 2008-04-19
Sorry, I missed that you were using hardy already. I assume you have your /etc/apt/sources.list up to date with the various repositories enabled. I don't have an answer. You could check launchpad to see if there is anything similar there. If there is, sometimes a 'work around'  is given. Sorry, I can't be of more help.

---

### Post by personal-data-removed on 2008-04-19
My repository sources list:

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

---

