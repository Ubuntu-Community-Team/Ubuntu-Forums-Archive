---
title: "DVD::RIP wont' install"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by eriefisher on 2006-03-04
Here's my console output:

dan@ubuntubox:~$ sudo apt-get install dvdrip
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  dvdrip: Depends: transcode (>= 2:0.6.14) but it is not going to be installed
E: Broken packages

So I tried to install Transcode:

dan@ubuntubox:~$ sudo apt-get install transcode
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  transcode: Depends: libdps1 (> 4.1.0) but it is not installable
E: Broken packages

So I tried to install libdps1:

dan@ubuntubox:~$ sudo apt-get install libdps1
Password:
Reading package lists... Done
Building dependency tree... Done
Package libdps1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdps1 has no installation candidate
dan@ubuntubox:~$

Here's my source.list maybe someone has an idea here:

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
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
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe 
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

eriefisher

---

### Post by Mustard on 2006-03-04
Have you changed your sources.list and then forgotten to do a sudo apt-get update first?

---

### Post by eriefisher on 2006-03-05
I do a sudo apt-get almost daily because I'm on dial up and don't want the updates to get too large. I thought it might be a sources.list problem but when I compared mine to some I see on line everything looks ok. Maybe someone will see something I don't.

eriefisher

---

### Post by Mustard on 2006-03-05
That being the case, it makes it a bit of tricky problem.  Have you had any other unofficial repositories enabled lately?

---

### Post by eriefisher on 2006-03-05
The only other repo I've had was for vlc, which I got from their site. It no longer works and I removed some time ago. This is the only app install I've ever had problems with in Ubuntu so it would be nice to get it figured out. 

Any suggestions would be welcomed.

eriefisher

---

