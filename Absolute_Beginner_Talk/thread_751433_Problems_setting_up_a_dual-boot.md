---
title: "Problems setting up a dual-boot"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by supersteviobros on 2008-04-10
I am looking to dual-boot Ubuntu and Windows XP(MCE)

I all ready have XP up and running.

I unfortunately do not have any options in setting up partitions when installing XP, because all I have are HP recovery discs, and they give no such options - they just reset everything on the hard disk to how it was when it was purchased.

I have been looking through Ubuntu installation tutorials, and most of them say to use the Guided resizing option, but I have no such option. Here are the choices I'm given:

> 
Guided - use entire disk
SCS|1(0,0,0)(sda) - 80.0 GB ATA ST98823AS

Guided - use the largest continuous free space

Manual


I do not want to use the entire disk, because I want to keep Windows installed.

When I choose the continuous free space option, I get the message:

> "Failed to partition the selected disk. This probably happened because the selected disk or free space is too small to be automatically partitioned.

So it seems my only other option would be the manual partitioning. Here is what I see when I choose that option:

[FONT="Courier New"]
> 

/dev/sda
	/dev/sda1		ntfs	/media/sda1	63926MB		18700MB
	free space					        8MB
	/dev/sda2		fat32	/media/sda2    15011MB	       14200MB
	/dev/sda3		ntfs	/media/sda3	1077MB		612MB
[/FONT]

Based on looking at the sizes, it appears that SDA1 is what Windows considers my "C:/" drive, with the Windows installation and programs. SDA2 appears to be the HP system recovery partition, and Windows considers this "D:/" I assume Windows is using the SDA3 as swap.

So what would be my best option? And why do I get no option for a guided setup of partitions?

---

### Post by tamoneya on 2008-04-10
your best option that will leave windows intact is to get an additional harddrive.  Then ubuntu can go on this harddrive and you dont have to touch any of the windows/HP partitions.  This would then become /dev/sdb.  You would then use the "use entire disl" option and tell it to use /dev/sdb

---

