---
title: "Dual Boot with XP"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by bmorberg on 2008-02-04
I tried to install Xubuntu Gutsy Gibbon with Windows XP already on a laptop.  I intended to have it as a dual boot laptop so I could play with Linux and learn some more about it.  I messed up the install and ended up partitioning my entire drive and installing Xubuntu while deleting Windows XP.  I just finished re-loading Windows XP on an NTFS partition and I still have Xubuntu on another partition.  I'm trying to figure out how to get to Xubuntu and create a dual boot option when power on my laptop.  Is there a guide someone could provide.  I assume I have to modify the MBR but I've never done it and have no idea how. When I boot from the Xubuntu install CD I can see both partitions (kind of cool since Windows would never let me see the linux partitions) and the info seems to be there.

---

### Post by Rocket2DMn on 2008-02-04
Yeah, when you installed windows again you overwrote the mbr so GRUB, the open source bootloader, is no longer used.  The upshot of that is, you boot directly into windows now!  Here is how to fix that:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4)

---

