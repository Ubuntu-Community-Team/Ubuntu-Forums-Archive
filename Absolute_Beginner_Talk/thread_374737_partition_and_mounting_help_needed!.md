---
title: "partition and mounting help needed!"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by deviouskoopa on 2007-03-02
i burned the ubuntu 6.10 cd and booted from it, and went through the first 3 steps easily. i have 2 partitions in windows xp pro, then i add 2 more, 1 for root and 1 for swap. i select ext3 for both of them. after it creates the 2 partitions, 20 gb for root and 2 gb for swap, it goes to the mount step, where i run into problems. i select the / mount point and the 20 gb partition, and the swap mount point with the 2 gb partition. then i hit forward but it says "FAT and NTFS filesystems may not be used on filesystems used by the system. It is usually best to mount them under /media/." i dont have any FAT or NTFS partitions selected though... so i hit back to step 4, and it says both of the new partitions i created are NTFS type!! i dont know why it changed it or what happened, or if im even creating the right partitions or setting the mount points right. im totally new to ubuntu, so im very confused as to why its not working.

thanks for any help at all!
-koop

---

### Post by taurus on 2007-03-02
Did you tell the installer to format / (20GB) as ext3 and the 2GB as swap?

---

### Post by Kateikyoushi on 2007-03-02
Try to delete those partitions, and make them again, if necessary reboot after deleting them, swap should be swap, / is ext3, also check that the windows partition's mount points are not set as / or swap but /media/XXX.

---

### Post by deviouskoopa on 2007-03-03
"Did you tell the installer to format / (20GB) as ext3 and the 2GB as swap?"

Yes, i set the 20 gb as ext3 and the 2 gb as swap.


"Try to delete those partitions, and make them again, if necessary reboot after deleting them, swap should be swap, / is ext3, also check that the windows partition's mount points are not set as / or swap but /media/XXX."

I tried deleting them and making the partitions again, but that didnt seem to work. I think my problem is that i set the mount points as / and swap instead of /media/XXX... should i just set the mount points to the default points given? for some reason i thought the mount points should be / and swap...

---

### Post by Patrick K on 2007-03-03
> then i add 2 more, **1 for root and 1 for swap. i select ext3 for both of them**. after it creates the 2 partitions, 20 gb for root and 2 gb for swap,Don't select EXT3 for the swap partition. Select swap.

---

### Post by deviouskoopa on 2007-03-05
alright thanks everybody, i got it to work :-)

---

