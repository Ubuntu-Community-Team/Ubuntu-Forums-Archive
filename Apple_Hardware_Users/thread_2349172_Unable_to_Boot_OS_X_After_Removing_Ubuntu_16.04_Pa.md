---
title: "Unable to Boot OS X After Removing Ubuntu 16.04 Partition Installed Via EFI"
date: 2017-01-11
forum: Apple Hardware Users
---

### Post by cal2u on 2017-01-11
Hi all,

SHORT VERSION:

I decided to dual boot Sierra and Ubuntu 16.04 using this guide ([http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf](http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf)), and everything worked fine. After deleting that partition, though, I'm no longer able to boot into OSX. Any help getting that partition bootable again would be greatly appreciated!

LONG VERSION:

After installing Ubuntu 16.04 onto a partition I created on my mac, I was able to boot into OS X by holding down the option key at startup and selecting "Macintosh HD" as my startup disk. This was without installing anything like rEFInd.

At this point there weren't any problems, but later I needed to have Ubuntu 14.04 instead of 16.04 installed, and the partition I had created for Ubuntu was too small. I wasn't able to remove the Ubuntu 16.04 partition using OS X's Disk Utility (a warning sign, maybe), so I booted up a Ubuntu 14.04 live cd and deleted the Ubuntu partition using gparted. At that point I wanted to resize my OS X partition, but Ubuntu wasn't able to do anything with my encrypted hsf+ partition, so I tried to boot back into OS X to resize it. I then discovered that I could no longer boot into OS X from the startup options menu.

I've installed Ubuntu 14.04 on my original 16.04 partition, thinking that perhaps it would magically make OS X bootable again on the startup options menu. Alas, the Ubuntu partition boots automatically, but Machintosh HD isn't an option when I boot up holding down the option key.

Any advice on how to boot into my OS X partition now? Doing a network recovery is an option I think, but I'm worried about losing files I have installed on my OS X partition.

---

### Post by cal2u on 2017-01-12
If anyone know any IRC channel that I might be able to get help on, that'd be helpful as well.

---

