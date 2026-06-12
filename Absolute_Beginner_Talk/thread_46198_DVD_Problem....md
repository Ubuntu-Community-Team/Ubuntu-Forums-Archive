---
title: "DVD Problem..."
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by cvogel on 2005-07-03
Hello all--

I have a small problem.  Last night I was able to place a DVD in my DVD-ROM and play the movie with no problems at all--except for DMA, that is.  I installed some updates from the repositories and the Ubuntu update manager, and now I can no longer play them.  When I place the DVD in the tray, Ubuntu brings up my CD/DVD Creator and renders the disc a blank DVD.  Does anyone know why this is happening and what I need to do to fix it?

Thanks

---

### Post by poofyhairguy on 2005-07-03
[QUOTE=cvogel]Hello all--

I have a small problem.  Last night I was able to place a DVD in my DVD-ROM and play the movie with no problems at all--except for DMA, that is.  I installed some updates from the repositories and the Ubuntu update manager, and now I can no longer play them.  When I place the DVD in the tray, Ubuntu brings up my CD/DVD Creator and renders the disc a blank DVD.  Does anyone know why this is happening and what I need to do to fix it?

Thanks[/QUOTE]

A. Try a reset.

B. can I see your sources.list?

sudo gedit /etc/apt/sources.list

to find it. paste it here.

---

### Post by cvogel on 2005-07-04
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by poofyhairguy on 2005-07-04
A. Delete that top line.

B. Hve you tried many different dvds?

---

