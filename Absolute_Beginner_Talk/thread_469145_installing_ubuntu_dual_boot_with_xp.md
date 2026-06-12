---
title: "installing ubuntu dual boot with xp"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-06-09
i have five partitions on my comp. xp is in the first one. i am currently in live cd mode trying to install ubuntu.

i want to install it in the second partition which is essentially D: in win environment. the partition thing in the installer is a bit confusing for me.

can anyone guide me how to go about it? the partition size is around 48 gigs. i want to dedicate this partition entirely to ubuntu...

---

### Post by ugm6hr on 2007-06-09
The easiest way to do this is by deleting your "D:" partition (making it unallocated free space), and then running the Ubuntu LiveCD installer with the "Guided - use largest continuous free space" option.  It doesn't give you the most control, and advanced users advocate a separate "/home" partition (a bit like a separate Windows "Documents and settings" partition), but is far easier.

Before I explain how it's done - be aware that this option will create 2 partitions in the newly created free space.  Which makes your current 5 partitions into 6.  If "D:" is currently a primary partition, and you already have 4 primary partitions, **DO NOT DO THIS**.

Also - probably prudent to backup important files before messing with partitions.
From the Ubuntu LiveCD - load GParted (appears as GNOME Partition Manager in the menu).
Find your "D:" partition - you chould be able to recognise it from the graphical display by size, location and filing system on the drive.  Chances are it is something like /sda2 or /hda2.
Right click on this partition, and delete or remove it.
Click Apply.

Exit GParted, and double-click the install icon.
Then follow the instructions, and select the "Guided - largest continuous free space option".

Hopefully, this will then just work.

PS: worth reading these instructions, just so you know what to expect:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Sushubh on 2007-06-09
[IMG]http://i11.tinypic.com/4yi1frl.png[/IMG]

so i delete HDA5 as per your instructions? i had like to have a home directory... how can i do that. 

i only have experience using ubuntu intsalled through grub. :)

---

### Post by ugm6hr on 2007-06-09
> **Sushubh said:**
> 
so i delete HDA5 as per your instructions?


Errrrmmmm. **NO**.

You have 4 logical partitions in the extended partition - so you can't create an extra in that space.  Your partitioning is going to be more complicated than normal.  Especially if you want a /home partition, and all of Ubuntu is to fit in the 48GB space.  I believe the rules are that each drive can have up to 4 primary and 4 logical partiions (in an extended partition).  So I'm not sure how you could manage to do this while maintaining hda1,6,7, & 8 without shrinking your extended partition and hda5, adding 2 new primary partitions (hda3 & 4) for "/" and "/home" and then making hda5 a "swap" partition within hda2.

Definitely not something to be undertaken without a decent backup of your data on the drive.

> **Sushubh said:**
> 
 i had like to have a home directory... how can i do that. 
I haven't done it myself - so I probably shouldn't advise you.  But this tells you how to do it after installing in a more normal fashion and it will be easier to follow this if you leave a partition available for /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Sushubh on 2007-06-09
see. this disk is brand new and just has xp installed on it. no data. i can go back to win and merge all the rest of the partitions into one big empty space. would that be the right way to go about installing ubuntu?

these partitions were created by the system guys...

---

### Post by ugm6hr on 2007-06-09
> **Sushubh said:**
> see. this disk is brand new and just has xp installed on it. no data. i can go back to win and merge all the rest of the partitions into one big empty space. would that be the right way to go about installing ubuntu?

these partitions were created by the system guys...

In that case - delete hda 5,6,7,8 and also hda2 - and start again.  As for how you would like your drive to be used - that's up to you.  Best to put some time into that decision before starting.  This might help:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

As a rule of thumb, if you're planning on allocating 48GB to Ubuntu - probably 1GB swap, 10GB for "/" and the rest for "/home" would be reasonable.  The rest of the disk could then be a spare data / backup partition (hda5 in example below).

Something like:
hda1: Windows (unchanged)
hda2: Ubuntu "/" - primary ext3 10GB
hda3: Ubuntu "/home" - primary ext3 37GB
hda4: extended (rest of free space)
hda5: whatever is left in hda4 - logical (file system of your choice - fat32/vfat reasonable)
hda6: Ubuntu swap - logical swap 1GB

Hope that helps.

EDIT:
Sorry - if you want to use the Guided install and then sort out your home partition later (which will probably be easier):
hda1: Windows (unchanged)
hda2: primary (file system of your choice - fat32/vfat reasonable) whatever space is left onHD
hda3: extended 48GB (contains hda5 & free space)
hda5: logical ext3 37GB (for future /home use)
which leaves 11GB free space within hda3 for the Guided installer (largest continuous free space) to put your swap and / directories (the swap will probably be closer to 500MB - which is plenty anyway)

---

### Post by Sushubh on 2007-06-13
cool got it working. thanks!

---

