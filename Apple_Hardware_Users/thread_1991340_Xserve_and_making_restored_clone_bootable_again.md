---
title: "Xserve and making restored clone bootable again"
date: 2012-05-30
forum: Apple Hardware Users
---

### Post by oldtechmage on 2012-05-30
I searched high and low for a solution but could not find one, so please forgive me if this is somehow a duplication of an existing answer.  I'm putting the answer out there in hope that if someone else is banging their head against this wall, this will save them the pain.

My goal was to take my cluster nodes, consisting of XServe 3,1 nodes with Ubuntu 11.04, and image a drive.  Then to take that image and put back on any node's drive and boot.  However, this did not work.  Even taking a working drive and putting it into another node didnt work.  It broke the boot.

Here is the workaround/fix I found:
- Assuming that you have imaged the drive and placed it into a node and you get the Question Mark Folder Icon...
- First obtain refIt, and make a CD of it.  This is on the site or can be found via a Inet search.
- Then boot the system, using the reFit disk, to the installed linux.
-  Next, from the root account (or sudo), you type grub-install (this will reinstall grub and fix the boot issue for this hard drive in this node)  Of course tweak settings as necessary for the node (IP, name, remove gridengine, etc.)
- Last, but not least, reboot the node w/o the reFit CD.

If all went well, then you will now have the node booting again, or have the image booting in a different node's hardware.

V/R
:guitar:

---

