---
title: "What's wrong with my sources.list"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by thinhlegolas on 2005-11-04
Hi, I'm using Ubuntu 5.10 Breezy Badger

Below is my /etc/apt/sources.list, i copied this from a website but now i realized it's for Hoary... so what should I do now?

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/ unstable/

## Backports
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

---

### Post by Ampersand on 2005-11-04
You just need to change every mention of hoary to breezy. Easiest way to do this is run
```
sudo gedit /etc/apt/sources.list
```
and use Replace from the Search menu (replacing hoary with breezy).

---

### Post by niko_ on 2005-11-04
i guess you only need to type something like this:

> 
sudo sed s,'hoary','breezy',g < /etc/apt/sources.list > abcd && sudo mv abcd /etc/apt/sources.list;

---

### Post by mikedtemple on 2005-11-04
The Debian Mallirat line shouldn't be there either.  Comment that out unless you're updating your Win32 codecs (to be able to play WMA, etc).  Otherwise, you'll break your system.  Debian isn't fully compatible with ubuntu.

---

### Post by thinhlegolas on 2005-11-04
thanks everyone :)

---

