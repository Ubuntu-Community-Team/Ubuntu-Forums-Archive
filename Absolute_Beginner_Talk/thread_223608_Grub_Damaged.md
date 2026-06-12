---
title: "Grub Damaged"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by Max Velocity on 2006-07-26
Hi, I keep getting an error to grub which stops me from booting apart from a live cd.

just shrinked my windows partition down a little (around 300megs) and made a new partition (fat32) and now grub seems to somehow corrupped itself.

I read and tried a few ways of repairing grub, but with no luck, And my only option left is to boot from the live cd

Windows Ntfs (20Gigs)
FAT32 (300megs)
Linux Swap (257megs)
Ext3 Xubuntu (7gigs)

I'm re downloading the Cd to try to install grub from there at the moment, but is there a safe way of fixing grub from the live CD?

---

### Post by Paerez on 2006-07-26
try this:
```
sudo grub-install /dev/hda
```

---

### Post by RavenOfOdin on 2006-07-26
My main comp has that same partitioning scheme.  I think you messed up the boot record and the locations that the GRUB entries point to by doing what you did.

I think the grub-install program is on the Live CD.  Just direct it to the partition that your Linux install is located on. Using the MBR is out since you're dual booting.

If you have a spare floppy disk, just install GRUB to /media/floppy0 or /dev/fd0 in order to prevent those complications in the future. Keep the disk in the drive when you want to boot Linux, take it out when you don't.

---

