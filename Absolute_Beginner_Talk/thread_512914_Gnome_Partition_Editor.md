---
title: "Gnome Partition Editor"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-07-29
So, I booted up from the LiveCD and I see a whole lot of options I'm a little afraid of.

I  don't want to format my Main HDD, I just want to format the slave drive.

Which option would I click to do  this, I want it in Ubuntu's defalt format.

Also I heard I  can rename both of the drives this way, since  Ubuntu wont let me through the system.

Neither of them have partitions and I don't want any on either. All I want to know is if I am going about formatting the right way. If there is an easier way to rename a HDD or format one through the system please let me know.

---

### Post by MicronXD on 2007-07-29
u have 2 HD's n u wanna format ur slave to ext3?

have u booted all the way to the gui? Gpart is really self explanitory select ur slave drive, then delete any partition u might have. then right click the empty space n then add partition... change the filesystem to ext3, n there ya go

---

### Post by stinger30au on 2007-07-30
if your really worried then unplug the 2nd hard drive, leave the main one in and go for it

---

### Post by bigfox on 2007-07-30
In the Gnome Partition editor at the upper left corner is a pull down that reads something like /dev/hda
/dev/hda should be the master drive
/dev/hdb should be the slave drive
This is assuming that your drives are IDE.

Mine is /dev/sda because the drive is SATA.  (It assigns them sdX because anything that is not IDE it thinks is SCSI.)

When you select one of the drives, check to partition layout to see if it matches the one you want to erase.  For instance partition size or total drive size.

---

