---
title: "Totally confused on partitiong new boot drive"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-12
I would like to install Ubuntun on my brand new 750GB SATA hard drive.  This drive will also be the main, bootable drive.

I confused as what is needed as far as partitioning is concerned.

Do I need a swap partition?  If yes, should the size be 2x current RAM?  Do I make it bootable?

I was told to make the logical (where the OS goes, correct?) about 20GB... is this supposed to be bootable?

The rest goes under primary, correct?  Do the primary and logical format under ext3?

Thanks for any help!!!

---

### Post by petercoh7 on 2008-03-12
AFAIK ubuntu will perform the format/partition when it's installed on the primary drive.  It did this when I installed on my hard drive.

---

### Post by A$h X on 2008-03-12
Ubuntu will perform the partitioning etc when it installs itself on the HD, or you could use gparted or partition magic to do it.

---

