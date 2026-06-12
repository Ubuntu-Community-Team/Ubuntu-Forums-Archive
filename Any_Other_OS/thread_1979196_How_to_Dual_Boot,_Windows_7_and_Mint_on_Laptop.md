---
title: "How to Dual Boot, Windows 7 and Mint on Laptop?"
date: 2012-05-12
forum: Any Other OS
---

### Post by ChrisNZ on 2012-05-12
We have a Asus Laptop Model K52J, that came with Windows7 (W7). I would like to set it up with Linux Mint v14 and retain W7 as well. Now I know there are some concerns about Windows being setup 1st as it seems to 'control' much of what you can load as a dual boot however how do I go about this?

1 - The Mint dvd will not Auto load as normal for some reason and I tried the shift+F8 to get into the bios but that didnt seem to work, so i couldnt changeto drive(E) to start the boot process 1st.
2 - I believe that part of the partitioning also retains the files of W7 for reinstallaion if it goes 'belly up' - how do I see it?

I have had a look here on the forums, however many situations have occurred with W7 and no two seem the same. 

How do I proceed here?

---

### Post by wilee-nilee on 2012-05-12
Look at the manual or the web for the bios command, and the per-session boot from menu not in the bios.

You want to get booted and first look at the HD and see if it already has 4 primary partitions, that is the max for a single mbr type HD set up. Use gparted in mint to look at the HD.

If you have less than 4 partitions then resize a partition in windows, not from the front of the partition though, and not the recovery partition, using its virtual disk manager, leaving an unallocated space for mint. Reboot windows to make sure its okay after resizing. Don't look for the partition count in windows it may not show all of them.

Then boot the mint again and choose the install to the free space in the install gui asking where you want it put. 

Personally I would use gparted to put a extended partition in that unallocated and a ext4 logical then the swap, then use the something other option if that is what it is called by mint, in the install gui with your choice of where you want the OS, basically the custom install, and install mint to the pre-formatted ext4. If you get this far make sure the grub bootloader is pointed at the mbr in that custom gui, open the partition from there and set the mount to / and the partition as ext4.

**Before doing any of this though I would back up the W7 completely, a whole image a clone and make a recovery disc if you don't have a install disc, this can be done in the W7 backup area.**

---

### Post by Perfect Storm on 2012-05-13
Moved to Other OS/Distro Talk.

---

