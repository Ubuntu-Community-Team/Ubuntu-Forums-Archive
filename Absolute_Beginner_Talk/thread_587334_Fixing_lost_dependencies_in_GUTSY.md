---
title: "Fixing lost dependencies in GUTSY"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Shlomir on 2007-10-22
Why is it there are so many lost dependencies since I upgraded to Gutsy?

I am trying to load some educational software and it needs all these Python dependencies, and then they need other dependencies.

DO you have to wait until GUTSY issues updates?

How do you fix the lost dependencies in one go , rather than have to search and load them all the time?

I find alot of 'libc' libraries missing as well, is this because the kernel has changed?

---

### Post by danbh on 2007-10-22
Whats the software?  Ill take a peak.

---

### Post by Shlomir on 2007-10-23
Basically the 'Childsplay' suite, it asked for libsdl-mixer1.2, libsdl-ttf2, libsmpeg0

The libsdl-mixer1.2 isn't available from the main Gutsy repo!

other dependencies missing are python-pygame and ttf-dustin

All went since upgrade to GUTSY

---

### Post by danbh on 2007-10-23
hmmm, it works fine for me.  I have those dependencies.  Maybe some of your repositories aren't enabled.  
Go to:
System > Administration > Software Sources
I would just enable all of the repositories, ie universe/multiverse/restricted.  And the same for updates too.

If that doesn''t work, please post the contents of /etc/apt/sources.list just so we can make sure.

---

### Post by Shlomir on 2007-10-23
Here are my source list, please post which ines I need to add if missing, cheers!

```
deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015)]/ gutsy main multiverse restricted universe
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse

```

:guitar:

---

### Post by Shlomir on 2007-10-23
Thanks for the tip, this is fixed now....I basically ticked ALL dependencies in 'Sotware Sources', even the unsupported ones or whatever, and all the libs installed!

Cheers!

---

