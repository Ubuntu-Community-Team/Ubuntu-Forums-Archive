---
title: "Where can I get xemacs ?"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by clenieralley on 2006-04-04
Where can I get an xemacs package to install on ubuntu?

---

### Post by karthik085 on 2006-04-04
Try search for xemacs, using apt-cache search or synaptic etc. They may be  available in different respo like universe, multiverse, etc.

[QUOTE=clenieralley]Where can I get an xemacs package to install on ubuntu?[/QUOTE]

---

### Post by carlosqueso on 2006-04-04
It's called xemacs21 in Ubuntu.  If you still can't find it, read on:


You need to make sure you have the Universe repository enabled.  Make sure your /etc/apt/sources.list file looks like mine (sudo gedit /etc/apt/sources.list)

```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse 
```

then type ```
sudo apt-get install xemacs21
``` to install it.

---

