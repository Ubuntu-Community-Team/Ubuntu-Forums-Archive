---
title: "Upgrade to Edgy"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by yerdon on 2007-02-15
Hey Everyone,

I'm running Dapper and trying to upgrade to Edgy using the instructions at:  [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

It starts fine and begins downloading stuff, however, half-way through it stops while trying to download something from packages.freecontrib.org and gives me this error:

Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out

I've waited a day to see if the servers were just down or something, but it is still doing it. Is there another way to do this?

Thanks!

Joseph

---

### Post by tronica on 2007-02-15
freecontrib is no longer i believe, heres the sources.list you would use from ubuntuguide.org

> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

then 

> wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

> sudo apt-get update

then 

> sudo apt-get dist-upgrade

that should do it

---

### Post by yerdon on 2007-02-16
Thank you!  I'm getting much further this time, but unfortunately, I'm getting the same type of errors with  security.ubuntu.com:80.  Any ideas?

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libbind9-0 1:9.3.2-2ubuntu3.1
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out

Thanks!

---

### Post by tronica on 2007-02-16
i haveing that too, must just be down.

---

