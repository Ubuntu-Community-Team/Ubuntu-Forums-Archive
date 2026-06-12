---
title: "Sources List for an AMD64"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by Maupertus on 2006-02-08
Although not truely a beginner, I was wondering what the recommended sources list was for a AMD64?

At the moment I have this one:

> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## official backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## amd64 users repository
##deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) hoary main universe multiverse restricted

## CVS snapshots packages
##deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) cvs main universe multiverse restricted

## amd64 packages testers repository
##deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) tests main universe multiverse restricted

I was wondering if I was doing something blatantly wrong ;)
Have to say my i586 list is much longer.

---

