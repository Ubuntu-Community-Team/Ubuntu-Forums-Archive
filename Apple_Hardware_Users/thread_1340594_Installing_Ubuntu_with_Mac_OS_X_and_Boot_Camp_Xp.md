---
title: "Installing Ubuntu with Mac OS X and Boot Camp Xp"
date: 2009-11-28
forum: Apple Hardware Users
---

### Post by Froobloops on 2009-11-28
I'm installing Ubuntu on a Mac that already has a boot camp xp partition and I need to use some of my Mac OS X partition for Ubuntu, that is, making another partition with some of the space that is currently being used by Mac OS.

How do I prepare a new partition without damaging any existing files in the Mac OS or Xp partitions?

---

### Post by linuxopjemac on 2009-11-29
I don't think that's possible.

---

### Post by Audiosears on 2009-12-10
Froob,

You should in fact be able to do this.  I followed [this]("http://www.maganti.info/2009/11/triple-boot-on-macbook-mac-osx-1061.html") guide to do a triple-boot setup on a 13" macbook (core duo x86) with Snow Leopard, Windows 7 Pro and Ubuntu 9.10.

You can set up the partitions yourself, but it's just as easy to install OSX and bootcamp windows first (as in the guide).  Then, use OSX's disk utility to reduce OSX's partition and set up a FAT32 partition with which you will later turn into an ext4 partition for Ubuntu (or other distro).  Check out this guide and I think you'll find you have already done the prerequisites and can start at step 1.

---

