---
title: "how to wipe hardrive in linux?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by ELD on 2007-09-18
Hi my brother wishes to wipe linux, but he doesn't have the net to downloaded gparted or anything.

And his windows recovery cd doesn't pick up linux partitions.

Any suggestions.

---

### Post by Jimmyfj on 2007-09-18
Gparted should be included on the live Cd - Else If you have an old Windows Cd, 98 and onward, Fdisk is able to delete non-dos partitions too.

Alternatively you can delete the partitions directly from the Live desktop

---

### Post by ELD on 2007-09-18
As far as i am aware gparted is not on live cd's is it?

He wants to basically wipe the hardisk and use his recovery cd, is there no actual way in linuc just to simply wipe everything??

---

### Post by hardyn on 2007-09-18
You want a blank disk?  is this disk your primary disk? or secondary?

if its your primary, you will have to use a boot disk, and if gparted is not on the disk, there is always good old fdisk, which im sure will be.  fdisk is a little clunky, but has worked in the unix world since the 70's  There is a more streamlined fdisk, but i don't remember the name.

---

### Post by Cato2 on 2007-09-18
The answer is simple, use the command line 'shred' tool.  I just did this a couple of times.

But **be very careful** if you have any other hard drives installed that you want to keep.

Basic steps are:

1. Type 'sudo fdisk -ul' - this shows you all partitions on all disks - note down carefully the exact disk name for the whole disk you want to erase - e.g. /dev/hdb for 2nd EIDE disk on primary controller.  You should be able to identify it by size and filesystem type, but if in doubt mount partition to check.

2. Type 'mount' - check that the disk partitions you want to erase are not mounted, umount if needed.

3. Now type 'shred -v /dev/hdb' (or whatever your disk is) - this will make 26 passes over your hard disk, taking a long time.  **This command does not prompt to make sure, it starts erasing immediately**

If you aren't quite so worried about data security, try 10 iterations - 'shred -v -i 10 ....'.  Goes a lot faster.

---

### Post by overdrank on 2007-09-18
> **ELD said:**
> As far as i am aware gparted is not on live cd's is it?

He wants to basically wipe the hardisk and use his recovery cd, is there no actual way in linuc just to simply wipe everything??

Hi you might have a look at this thread
[http://ubuntuforums.org/showthread.php?t=496856&highlight=command+for+wiping+hard+drive](http://ubuntuforums.org/showthread.php?t=496856&highlight=command+for+wiping+hard+drive)

---

### Post by bodhi.zazen on 2007-09-18
1. Gparted is on the Ubuntu desktop (live) CD. You can format the linux partiton as FAT or NTFS.

2. Or you can format the partition from windows itstelf (under disk management).

3. After you reformat the Ubuntu partition you will need to re-install the Windows boot loader.

See if this link helps : [HowTo: Remove Ubuntu (& Restore Windows)](http://ubuntuforums.org/showthread.php?&t=508927)

---

