---
title: "Stuck with old distro (DSL probably)"
date: 2012-05-14
forum: Any Other OS
---

### Post by martinmolema on 2012-05-14
Hi all,

Recently acquired an old WYSE terminal and got it to work with Linux. A small word about the boot proces: the WYSE WinTerm 3200LE boots some bootloader that starts looking for an USB-stick. Once found it boots the linux installed on the USB stick.

However, it is an almost completely stripped down version. Understandable because system specs are out-of-time. But I would like to add a few simple components. Install via apt-get install should work, but then I need a source with the old version used. The sources.list says:
deb [http://archive.debian.org/debian-archive/](http://archive.debian.org/debian-archive/) woody main contrib non-free
deb [http://mirror.aarnet.edu.au/debian](http://mirror.aarnet.edu.au/debian) oldstable main contrib non-free
deb [http://mirror.linux.org.au/debian](http://mirror.linux.org.au/debian) oldstable main contrib non-free
deb [http://mirrors.usc.edu/pub/linux/distributions/debian](http://mirrors.usc.edu/pub/linux/distributions/debian) oldstable main contrib non-free

After logging in it says DSL, so probably Damn Small Linux variant.

Three questions:
- is there a way to upgrade to a more recent version?
- or is there a way to get the old archives? I already have a Hardy Heron location with all the archives from the live-cd, so setting up one for this old one shouldn't be a problem (I hope).
- is there a way to determine how to setup a new boot-sequence (the second boot part) on my USB stick according to a file list from the current setup?

Any help is greatly appreciated!

---

