---
title: "edgy sources.list advice"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-11-20
I just reinstalled edgy and I'm wondering what a good sources.list would be? Thanks

---

### Post by LLRNR on 2006-11-20
Hi! Since I'm not running Edgy myself, [this](http://ubuntuforums.org/showthread.php?t=265326) is the best I could find. I hope it will help you someway or another!

---

### Post by nickpaton on 2006-11-20
Each sources list is individual, outside of the core packages which are required.

The extras I've added are needed for the extra packages I run on Edgy, but here goes:

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

## Automatix
deb http://www.getautomatix.com/apt edgy main

## Samba
deb http://www.linux2go.dk/ubuntu edgy main
deb-src http://www.linux2go.dk/ubuntu edgy main

## OpenOffice.org
deb http://people.ubuntu.com/~doko/OOo2/ ./
deb-src http://people.ubuntu.com/~doko/OOo2/ ./

## VLC nightlies (GPG: 81CACA84)
deb http://nightlies.videolan.org/build/dapper-i386 /
deb-src http://nightlies.videolan.org/build/dapper-i386 /

## Bleeding Edge Drivers
deb http://www.albertomilone.com/drivers/edgy/legacy/32bit binary/
deb http://www.albertomilone.com/drivers/edgy/nonlegacy/32bit binary/
deb http://albertomilone.com/drivers/unstable/edgy/32bit binary/

## Seveas' packages (GPG: 1135D466)
deb http://seveas.theplayboymansion.net/seveas edgy-seveas all
deb-src http://seveas.theplayboymansion.net/seveas edgy-seveas all

# -------------------------------------------------------------------------------------------------
# gpg --keyserver subkeys.pgp.net --recv <KEY>; gpg --export --armor <KEY> | sudo apt-key add -
```

Psychocats has a good sources list "starter" from where you can add as you need to:

[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

And finally the biggest one this side of the Limpopo (but don't install all of it!):

[http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html]("http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html")

---

### Post by cptjaben on 2006-11-20
Thanks for the help everyone.

---

### Post by alynx on 2006-12-05
ye , thanks for this post.  I finally got my sources list back together after i tried to go over to edgy

---

