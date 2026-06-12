---
title: "BitTorrent updates"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by webjames on 2007-03-12
hi, i think this is a little problem

a pop up appeared saying i had updates so i clicked on it and it has two, one automatix, and the other bittorrent. i cannot tick the bittorrent update.
when i go into synaptic and click update this come up:

bittorrent:
  Depends: python (<2.4) but 2.4.3-11ubuntu3 is to be installed

also when i try to install the bittorrent gui this comes up:

bittorrent-gui:
  Depends: bittorrent (>=4.4.0-2~sarge) but 3.4.2-6ubuntu3 is to be installed

what is going wrong, have i not got something i need?

thank you :)

---

### Post by taurus on 2007-03-12
Did you mix Debian repos with Ubuntu?  What does your /etc/apt/sources.list look like?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Kateikyoushi on 2007-03-12
Could you show us your sources.list ?

```
cat /etc/apt/sources.list
```

---

### Post by webjames on 2007-03-12
well i got onto automatix and removed it's repos via it's menu. the bittorrent update has now gone. now i can install the gui, but i wanted the latest bittorrent like on [http://www.bittorrent.com/download](http://www.bittorrent.com/download) so i download the debian package but it says it's incompatable. hmm... what now?

here is my sources:

> james@james-ubuntu:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) edgy exailedeb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
james@james-ubuntu:~$ 


thank you! :)

---

### Post by Kateikyoushi on 2007-03-12
Do not mix debian packages and ubuntu packages, wait till the app gets updated.

If you really insist to get that version you have to download and install the dependant packages as well by hand, but do not be surprised if things break after that...

---

