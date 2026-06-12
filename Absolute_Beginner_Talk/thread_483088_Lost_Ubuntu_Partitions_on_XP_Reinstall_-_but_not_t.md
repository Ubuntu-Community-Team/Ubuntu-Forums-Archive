---
title: "Lost Ubuntu Partitions on XP Reinstall - but not the usual solutions"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by ChrisMoore0908 on 2007-06-24
Having spent 2 weeks trying to solve this problem, perhaps someone can point me in the correct direction.

History. Installed Ubuntu on a a 200GB hard disk, which had XP home already installed. Ubuntu installed perfectly, even detecting the XP and importing desktop settings. One happy punter. Grub gave options for Ubuntu or XP Home on boot.

Decided to rebuild XP. Slipstreamed latest XP SP2 updates etc and rebuilt a new XP Home installation CD. Used **ACRONIS PARTITION EXPERT** to resize partitions to produce a new WINDOWS DATA drive. So at that point had C drive, F Drive (windows data) and 3 Linux partitions for Ubuntu.

Reinstalled XP into C drive. All OK (meaning had new shiny XP and windows data partition.

Now the problems start. Firstly, GRUB disappears. Expected this. Tried to recover GRUB with **SMART BOOT MANAGER** and **SUPER GRUB**. In both cases, couldnt recover GRUB. Eventually resorted to using the UBUNTU bootable CD, and recovered GRUB from there. But NOW GRUB runs on boot, but the linux partition listed cannot be mounted. FYI, the XP home entry works fine.

Now, if I try to "find" my linux partitions, using either fdisk-l or Acronis Partition Expert, I am told that I have the following:

Device       Boot?       Start      End      Blocks         ID     System
/sda1          *            1             7995  64219806    7       NTFS
/sda 2                       7996      24321  131138595  5      Extnd
/sda 5                       7996      13219   41961748   7      NTFS
/sda 6                       24087    24321   1887606     82   Linux Swap

So, where is the rest of Linux?

---

### Post by ChrisMoore0908 on 2007-06-24
One more thing. If I try to reinstall Ubuntu from scratch using a Live CD, it no longer detects ANY partitions on the hard disk, either Windows or Ubuntu??!!??

---

### Post by southernman on 2007-06-24
Your linux partitions are in /sda2, from what I see. It's an extended partition that appears to house sda3 and sda4. My guess is those would be your / and /home folder.

---

### Post by ChrisMoore0908 on 2007-06-24
Excellent News. Now, how do I get GRUB to boot one of those?

---

### Post by southernman on 2007-06-24
I am not profecient enough to help you, but use [this guide]("http://users.bigpond.net.au/hermanzone/p15.htm"), it's the one I've used in times of grub woes or just tweaking grub.

---

### Post by freebird54 on 2007-06-24
From what I can see there, you have misplaced (lost) the Linux partitions inadvertantly.  The numbering of the partitions is correct for this scenario (sorry!) - as more than likely the partitioner you were using actually converted the Linux partition INTO an extended one (rather than moving it or resizing or whatever you intended for it to do.

There actually is unnaccounted for space on the drive (which might be your missing partition) from block 13220 to 24086.  However, I don't have Acronis, and can't tell you what's going on with it.  Perhaps, using it, you can remind it that this partition is to be active/unhidden or whatever is currently not allowing it to show.

It is not a good sign that GPartEd doesn't see ANY partitions - unless you are looking for it when the drive is already mounted.  Then it won't show you anything...

Good Luck!

---

