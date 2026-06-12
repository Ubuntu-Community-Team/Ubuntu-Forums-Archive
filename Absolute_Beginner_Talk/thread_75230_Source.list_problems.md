---
title: "Source.list problems"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-10-13
I just tried to ```
 sudo apt-get update, sudo apt-get upgrade. & sudo apt-get dist-upgrade
``` And its having some issues connecting to some of the security downloads.

here is my sources.list:
```

## deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted

## All officially supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://ubuntu.tower-net.de/ubuntu/ hoary java

## The source pacakges
#deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
#deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
#deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## All community supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse

## The source pacakges
#deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse
#deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse

## hoary-extras - the most widely used source for packages not includded in Ubuntu
## no guarantees on working - not enabled by default
deb http://public.planetmirror.com/pub/ubuntu-backports/ breezy-extras main universe multiverse restricted
```

Could anyone post their sources.list from the new release of breezy?

---

### Post by TristanMike on 2005-10-13
You may just have to be patient whilest the breezy rush is on. :) I've had some issues with apt-get update.

---

