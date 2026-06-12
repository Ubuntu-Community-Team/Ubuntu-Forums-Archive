---
title: "PPC repository question, can somebody please post a good sources.list?!"
date: 2009-03-02
forum: Apple Hardware Users
---

### Post by stir-crazy on 2009-03-02
My wife, bless her heart, wanted a clamshell iBook (300Mhz G3, 577 MB RAM,  Ubuntu 8.04) because it was cute...nevermind it's limitations.  Makes my job fun.  But the past several months, the repositories fail me all the time. :mad::mad::mad::mad::mad::mad::mad::mad:

I upgraded the hard-drive, since there was no real information of value (or so I thought), I didn't bother transferring any information to a flash drive or anything.  Now, I can't get great applications like alexandria to install on her machine, which I had before I bumped her up from a 6 GiB hard-drive.

I even get these security updates that Synaptic wants to install (how did it find them?!), but can't due to the sources status.

So, if somebody could just make life easy and post a functioning, and as comprehensive as possible sources.list, I'd be very appreciative.  If anybody knows how to get awn working on this fossil of a laptop, please let me know that too!

Thanks so much in advance!

---

### Post by avtolle on 2009-03-03
Here is mine for 8.04.

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy main restricted
deb-src [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-updates main restricted
deb-src [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy universe
deb-src [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) hardy universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-updates universe
deb-src [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy multiverse
deb-src [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) hardy multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-updates multiverse
deb-src [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' respository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canoncial.com/ubuntu](http://archive.canoncial.com/ubuntu) hardy partner

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-security main restricted
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-security main restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-security universe
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-security universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-security multiverse
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-security multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-proposed restricted main multiverse universe

---

### Post by stir-crazy on 2009-03-09
Thank you!  This looks very promising from my initial tests here; found Alexandria and it's related packages, we'll see about updates and what not next.  Very helpful, thank you!

---

### Post by J_Random on 2009-04-18
Greetings!
Now, can someone please post working ppc repos for 8.10.
My Synaptic complaining about wrong signatures, and not updated repos. Thank you in advance!

---

### Post by stream303 on 2009-04-18
About Synaptic - in some cases, especially where one has upgraded from older versions, you may have to put your ppc repositories in the "third party software" tab, instead of in the main software tab.

You'll still need to make sure that you are pointing to the ubuntu-ports repos instead of the very old original ports years ago.

New installs may not need this work-around - I haven't tried Jaunty yet.

---

### Post by thatguruguy on 2010-01-10
Would someone please provide the sources.list for karmic on a power pc?  My wife's software sources listing is completely borked.

---

### Post by othiena on 2010-01-20
If you want the karmic repositores just replace hardy with karmic. That goes with the other versions of ubuntu just replace hardy with the first word in the distrobution. For example Lucid Lynx repositores would be```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ports.ubuntu.com/ubuntu-ports/ lucid main restricted
deb-src http://ftp.usf.edu/pub/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ lucid-updates main restricted
deb-src http://ftp.usf.edu/pub/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ports.ubuntu.com/ubuntu-ports/ lucid universe
deb-src http://ftp.usf.edu/pub/ubuntu/ lucid universe
deb http://ports.ubuntu.com/ubuntu-ports/ lucid-updates universe
deb-src http://ftp.usf.edu/pub/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ lucid multiverse
deb-src http://ftp.usf.edu/pub/ubuntu/ lucid multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ lucid-updates multiverse
deb-src http://ftp.usf.edu/pub/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ lucid-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' respository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canoncial.com/ubuntu lucid partner

deb http://ports.ubuntu.com/ubuntu-ports/ lucid-security main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ lucid-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ lucid-security universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ lucid-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ lucid-security multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ lucid-security multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ lucid-proposed restricted main multiverse universe 
``` notice that I put lucid in place of hardy

---

