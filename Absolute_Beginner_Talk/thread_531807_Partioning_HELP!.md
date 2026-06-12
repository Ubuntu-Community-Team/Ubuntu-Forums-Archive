---
title: "Partioning HELP!"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Noobuntu61 on 2007-08-22
[SIZE="4"]Hey guys i have another question. I have a 120 GB ata hard drive with C and D drives for a windows vista laptop. Linux using the guided partioner wants to use the whole 120 but i would like to dual bot setting aside about 20 GB for linux. What is the best way to do this? And how do you do this?

I have a lot of files that i need on the vista hd and i have no reinstallable version of vista (manufacturers don't include it in purchase). Thanks for any help in advance.[/SIZE]

---

### Post by wieman01 on 2007-08-22
You could boot up Ubuntu using the Live CD and fire up GNOME partition manager. That lets you partition your drive and install Ubuntu on it.

Alternatively get a copy of PartitionMagic for Windows which does a similar (good) job.

---

### Post by HW_Hack on 2007-08-22
I have no Vista experience - but heres how I do it with XP  - 

The D: partition is a bit strange you can keep it or delete it to make space - the goal of the steps below is to cram your files near the start of each partition so you can shrink the physical partitions and make space for Linux

1. hopefully you have some experience making bootable CDROMs using  .iso  files ----- google for GPARTED and down load the  .iso   --- create a  GPARTED CDROM.  GPARTED is an essential tool for working with partitions be they Linux or NTFS etc.

2. I then run the hard disk utilities in XP (clicking properties on the hard drive)
               - Run the disk checker first to check / test clusters etc.
               - Next do a defrag to pack all your files + data (this will actually pack all your files near the start of the windows partition.

3. Back up your data just in case 

4 Boot GPARTED ---- on the graphical display you should see your hard drive listed as hda - and in yellow you see the amount of space (and location) of the files on your C:/D: partitions 

5. click on the desired partition and then I thinks you click edit -- a new window opens showing just that partition -- put the cursor over the right side of the partition edge and you can literally click-n-drag the partition edge to the left making the partition smaller.  click OK

The cool thing about GPARTED is its very safe - because nothing really happens to your disk until you click the big Apply button - so feel free to fiddle around a bit

As you shrink partitions you will gain free space on the drive --- 10 or 15 or 20GB is fine for a Ubuntu install --- when reay hit the Apply button and say yes - GPARTED now adjusts your partitions. You should end up with a grey space on the right side of the display that is Free Space.

Now try the install program - choose use the largest area of free space to install Ubuntu  - Ubuntu will automatically setup a  / mount point and a swap partition --- and will plop Grub onto your boot sector for dual booting 

good luck

---

