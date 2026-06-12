---
title: "Multi-boot"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by avro on 2007-05-04
I have my Dell set up to dual boot Windows and Suse Linux but I would like to have a try with the latest Ubuntu.  Do I have to delete the Suse partition or can I add an Ubuntu partition that would still let me boot Windows when I need to but be able to choose either Ubuntu or Suse  :confused: ? 

or do I need to delete the Suse partition?  :confused: 

Thanks for any help.

Brian in Bruggen

---

### Post by xboxbman on 2007-05-04
You should be able to make another partition with the ubuntu live/installer cd, as long as you have enough drive space.  I don't know much about Suse, but i'm assuming it uses GRUB, which would detect ubuntu once installed.  If you don't have enough room to create a new partition for ubuntu, the live disk has partition tools to change the size of your other partitions to make room.

---

### Post by starcraft.man on 2007-05-04
> **avro said:**
> I have my Dell set up to dual boot Windows and Suse Linux but I would like to have a try with the latest Ubuntu.  Do I have to delete the Suse partition or can I add an Ubuntu partition that would still let me boot Windows when I need to but be able to choose either Ubuntu or Suse  :confused: ? 

or do I need to delete the Suse partition?  :confused: 

Thanks for any help.

Brian in Bruggen

Just curious but what boot loader are you using? I never tried suse (should one day...). As for do you have to delete suse, I don't see why. As long as you have 8-10 GBs of clear space on one of your drives you can make a simple two partition drive. (1 root directory (/), primary partition formatted 6 GB with Ext3, and then a simple 2 GB swap file partition).

The easiest way to try it first though is to just pop in the Live CD.

Plenty of choices on how to try :)

---

### Post by NICU on 2007-05-04
You don't have to uninstall/delete anything as long as you have enough free space.  As always - backup everything you don't want to lose... 

Depending on your hard drive space you may just be able to create a new partition (its best to have a few gigs of free space).  If your hard drive doesn't have any empty partitions you will have to resize and move your existing partitions.  All of these methods can be accomplished using a LiveCD and a few Google searches will tell you in better detail exactly which steps to take. 

On my desktop PC I have Windows XP, Ubuntu, and SUSE all installed.  I installed Ubuntu, then Windows, then SUSE.  SUSE's configuration utilities recognized all of my other OSes and configured GRUB for me successfully so I know of anything in particular to tell you to watch out for.

---

