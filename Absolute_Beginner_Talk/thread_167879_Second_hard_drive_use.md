---
title: "Second hard drive use"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by pshnfry on 2006-04-29
I've added a second hard drive and partitioned as Ext2 using Gparted.  I've then used System/Admin/Disks to mount.  I can't save to or browse the folder via places, as I'm not the owner.  chown --help is not helpful. I found a Linux tutorial which contained enough info to enable me to use chown, I can now browse and move files to the folder on hdb, but Disks and Gparted both tell me 600mb is used when I can only see <10mb used by browsing.

What's going on?

Any pointers to a disk management and/or concepts tutorial in Linux?

I suspect it might be possible to resize and move partitions to more efficiently use the available space as this box is limited to 6gb total. 

(Another late night looking for answers that should be easier than this! I do like Ubuntu Breezy/Gnome but the constant searching for simple tasks with hardware compatibility, drivers, administration is wearing me down.)

:-({|= :-({|= :-({|=

---

### Post by pshnfry on 2006-04-29
bump

---

### Post by Sutekh on 2006-04-29
I was just replying...

The difference in reported usage (from Disks and GParted) to what you can see, is most probably the overhead from the filesystem formatting.  All filesystems have some.

---

### Post by stoeptegel on 2006-04-29
Yeah, my fresh formatted ext3 300GB harddisk also used like 15GB already when there weren't any file on it yet.

---

### Post by Sutekh on 2006-04-29
Yep even more so for a journalled filesystem, like ext3 and a massive hard drive.

---

### Post by pshnfry on 2006-04-29
So a 2gb hard drive should be expected to lose more than 25% to file system overheads?

This is a minimalist pc set up for browsing, downloading, e-mail and Linux learning.  How can I more efficiently use a 4 and 2 gb hdd under Ubuntu Gnome? Currently set up as hda1 3922 ext3 (2514mb used), hda2 196 extended and hda5 linux-swap.  I think these last two are shared? hdb1 2008mb ext2 (which now shows only 32 mb used (i don't know where the 600mb used went to between last night and this morning?)

Any suggestions on set up or pointers to tutorials?

---

