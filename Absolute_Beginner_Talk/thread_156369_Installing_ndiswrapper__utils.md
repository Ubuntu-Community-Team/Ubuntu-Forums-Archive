---
title: "Installing ndiswrapper / utils"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by robTard on 2006-04-06
I've used synaptic to get ndiswrapper, and now am trying to get ndisgtk which shows up under synaptic, but ndiswrapper-utils is not showing up...  I have installed the extra repositories... Any idea for nub?

---

### Post by benfinkel on 2006-04-06
I'm having the opposite problem...

I got utils and gtk, but I cannot find ndiswrapper lol


How did you find ndiswrapper?  When I searched for 'ndiswrapper' I only found the gtk and the utils.

---

### Post by taurus on 2006-04-06
[QUOTE=benfinkel]I'm having the opposite problem...

I got utils and gtk, but I cannot find ndiswrapper lol


How did you find ndiswrapper?  When I searched for 'ndiswrapper' I only found the gtk and the utils.[/QUOTE]
Did you remember to comment out by removing the # sign in front of all the lines for universe and multiverse in /etc/apt/sources.list?

---

### Post by robTard on 2006-04-06
here is a copy of my sources.list
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by benfinkel on 2006-04-06
Mine looks the same and I still cannot find ndiswrapper ](*,)

---

