---
title: "remove grub and kubuntu"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by healingdread on 2007-09-12
i have a dual boot system with winXP on one hard drive and kubuntu on the other
i want to completely remove kubuntu and grub to free up storage
how do i do this?
i have another system with kubuntu on now!!!!!
keep it simple guys:confused:

---

### Post by bone2006 on 2007-09-12
If your removing the boot loader grub, what's your other operating system?  If it's wnidows, you'll need to repair the master boot record since you don't want to use grub anymore.

To remove the kubuntu partition, get gparted liveCD, just do a search in google it's easy to find.  Boot up and it's really easy to use, just remove the ext2 or ext3 partition and then increase the size of your other partition.  At this point nothing will probably boot up since you removed grub.

If you have windows XP I believe you can type in fdisk /mbr to repair the master boot record or there should be a repair in windows xp when you boot up.

Why are you removing kubuntu if you don't mind me asking?  Just curious

---

### Post by hyper_ch on 2007-09-12
once you booted into windows open a terminal and enter:

```

fixmbr

```

that should overwrite grub with the windows bootloader...

Reboot after that and see if you get the "normal" windows boot manager thingy... if so, then you just delete the existing Ext3 and Linux Swap partitions and make them Fat32 or NTFS and that's it.

---

### Post by Irony on 2007-09-12
The simple way;

[PHP]Boot from XP installation disc > press any key on prompt to boot from CD > after some time options appear, press R for recovery console > press 1 to select Windows > admin password, enter if no password > at the command prompt type fixmbr > warning given, hit y for yes, hit enter > at prompt type exit > eject disc[/PHP]

Now boot up into windows go to disk management/computer administration which is somewhere in Start and format the spare partition.

---

### Post by bone2006 on 2007-09-12
thanks for that info hyper_ch, it has to be the easiest way I've seen...good to know

---

### Post by LaRoza on 2007-09-12
If you don't have the install disk, use the Super Grub Disk to restore the Windows MBR, then use XP's disk management to delete or reformat the Ubuntu partition.

---

### Post by ubDed on 2007-09-28
i have to thanks Irony, because I was able only to boot up system from cd and that was the only way to restore windows (some problems with grub and Gutsy installation)

---

