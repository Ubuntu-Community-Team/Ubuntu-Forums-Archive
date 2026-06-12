---
title: "Installing 32bit onto external HD on iMac"
date: 2009-07-11
forum: Apple Hardware Users
---

### Post by adverto:veritas on 2009-07-11
Hello. I was wondering if there were a way to install Ubuntu 9.04 to an external HD. I have a 60GB ext HD that can be used as a bootable drive. I'm just not sure how to put the install image on it. I thought about partitioning the drive with one partition for the installer to run from and the other allocated as freespace or a mapped partition for the OS. I've downloaded the 32bit install from ubuntu.com. Anyone got any suggestions on how to do this?? Thanks!!
-newb

---

### Post by hajk on 2009-07-11
If your iMac is a MacIntel machine, then you could *install* Ubuntu on an external HD without any problem... but you wouldn't be able to *boot* from it due a limitation in the Apple implementation of EFI (the BIOS replacement). Now, that last bit isn't entirely true: there is a new version Grub2 around (not part of the default Ubuntu installation) that should, when completely matured, allow booting from an external HD with GUID partition table. If you're interested, there's an active thread here on that subject. 

If, OTOH, your iMac is an older PPC machine, then someone else should provide an answer...

---

