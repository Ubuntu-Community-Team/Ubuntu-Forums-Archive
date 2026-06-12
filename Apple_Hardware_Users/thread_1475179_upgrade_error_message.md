---
title: "upgrade error message"
date: 2010-05-06
forum: Apple Hardware Users
---

### Post by anurse on 2010-05-06
Hi!

When I go to upgrade to lucid (fr 9.10) via the update manager I get this message:

:Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/lucid/Release](http://ports.ubuntu.com/ubuntu-ports/dists/lucid/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

The proviso before the error message says this:

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

But I don't think it can be a network problem. Suggestions about what I am doing wrong or what I need to fix? 

Best
Andrew

---

### Post by linuxopjemac on 2010-05-07
Show us your sources.list,  this is the usual place to look at:

```
cat /etc/apt/sources.list

```
copy and paste it here pls

---

### Post by anurse on 2010-05-07
Here it is (thanks in advance, btw, for your help)

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic main restricted
deb-src [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic-updates main restricted
deb-src [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic universe
deb-src [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) karmic universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic-updates universe
deb-src [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic multiverse
deb-src [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) karmic multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic-updates multiverse
deb-src [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' respository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canoncial.com/ubuntu](http://archive.canoncial.com/ubuntu) karmic partner

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic-security main restricted
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic-security main restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic-security universe
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic-security universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic-security multiverse
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic-security multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) karmic-proposed restricted main multiverse universe

---

### Post by linuxopjemac on 2010-05-07
I don't see a problem here

---

### Post by anurse on 2010-05-07
Indeed. What would happen if I changed Karmic to Lucid in the source.list?

---

### Post by linuxopjemac on 2010-05-07
Do you really want to do that ? Then you upgrade your whole box to Lucid Lynx. I would not do that as it will give you trouble.

---

### Post by anurse on 2010-05-07
So ... clean install is the better way to go?

---

