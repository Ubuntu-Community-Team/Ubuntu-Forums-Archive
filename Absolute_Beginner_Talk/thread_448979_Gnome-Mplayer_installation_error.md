---
title: "Gnome-Mplayer installation error"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Limitlesschannels on 2007-05-19
during source installation I received this error for a missing dependency:

checking for GNOME... configure: error: Package requirements (libgnome-2.0 libgnomeui-2.0 ) were not met:

No package 'libgnomeui-2.0' found

I haven't been able to locate that library through either a package search or random permutation guessing through apt-get, help please.

---

### Post by taurus on 2007-05-19
Which release are you running and can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by wormser on 2007-05-19
In my signature there is a great tutorial on setting up mplayer.

---

### Post by Limitlesschannels on 2007-05-22
Here is my sources.list.  I will check out the tutorial while awaiting a response.


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#ADDED 20APRIL2007 FOR DEBUNTU.ORG REPO
deb  [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse

#ADDED 20 APRIL2007 FOR MEDIBUNTU MULTIMEDIA UPDATES
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
#AUTOMATIX REPOS END

# Ubuntu Satanic Edition ADDED 4MAY
deb [http://parker1.co.uk/hell](http://parker1.co.uk/hell) feisty main
deb-src [http://parker1.co.uk/hell](http://parker1.co.uk/hell) feisty main

# ADDED 5MAY BY FOR CINELERRA
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./

---

