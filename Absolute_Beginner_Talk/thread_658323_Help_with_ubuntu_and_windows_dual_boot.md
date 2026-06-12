---
title: "Help with ubuntu and windows dual boot?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by huntnplay on 2008-01-04
hi guys, i tried using ubuntu on my sony vaio laptop, but didn't get used to the fact that many of the keys didn't work, and i was more comfortable with windows software, but i want to use ubuntu. i have a family computer that i want to install ubuntu on, i already tried once. i want to dual boot it with windows xp, it already has xp, and 80gb hdd, i wanted to allot 35gb to ubuntu, and so i partitioned my c://. then when in stalling ubuntu, i did some weird thing, it didn't make sense, and finally, kept saying no space left, then when i rebooted it gave me a boot error, couldn't boot into xp or ubuntu, the ubuntu installation didnt go well. but i want to do it properly, so if someone could guide me, it would be great. tia.

---

### Post by Kobalt on 2008-01-04
Hello,

If you need some help, you should try to [check this out]("http://www.psychocats.net/ubuntu/partitioning") first, it's about partitionning. You will also find some detailed guides about installing Ubuntu there.

---

### Post by scizzo on 2008-01-04
Remember to install windows and then ubuntu. If you install windows after the ubuntu install it will override the MBR and ubuntu might not be bootable.

Ubuntu MBR is much nicer.

---

### Post by DishBreak on 2008-01-04
indeed. a partition editor is a weapon of mass destruction. Usually, you will back up your data and reinstall windows then ubuntu. 

live and learn. =)

---

### Post by huntnplay on 2008-01-04
kobalt, thanks for the link. it was very insightful. i already have windows on the pc. its a 80gb drive, and i want about 35gb partitoin alloted to ubuntu. so should i do all that was on the link thru the cd, or should i partition the drive beforehand into 45gb-35gb? and thats where im having the problem. last time i already did the partition using partition magic, then when i went to select the drive during ubuntu installation, it kept saying, root thing invalid. then the installation was wrong, when rebooted, there was booterror, couldn't login to either ubuntu or windows, had to reformat windows. i want to avoid this problem, and make it problem free, my parents use windows on this computer. so it shouldn't create a problem.

---

### Post by lswest on 2008-01-04
you could try, during the install from the liveCD, to choose "edit partitions manually" and resize the XP drive, and use that to create a swap partition and a / filesystem, optionally also create a /home partition.  Be sure to specify the mountpoints of the different partitions during the install.

---

### Post by insertAlias on 2008-01-04
Well, if you don't mind reinstalling windows again, you could partition the drive during the windows install (with 35 gb of free space) and then install Ubuntu onto the free space.  Do it in that order, so grub becomes the bootloader. (The windows bootloader can't boot anything but windows.)

Alternatively, you could use something like Partition Magic or Acronis Disk Director (neither is free) to non-destructively resize your partition,  if you feel comfortable with that.  Both work fine.

---

### Post by lswest on 2008-01-06
i want to point out that i have successfully partitioned XP with grub before, so you could try, after backing it up, to resize it with gparted in the liveCD.

---

### Post by Sbarton on 2008-01-06
If you have'nt yet seen this site it deals with XP/Ubuntu dual booting.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

regards

---

### Post by BL00dFox on 2008-01-06
> **DishBreak said:**
> indeed. a partition editor is a weapon of mass destruction. Usually, you will back up your data and reinstall windows then ubuntu. 

live and learn. =)

Not really. Most things you do with a partition editor can be undone, like if you deleted a vital partition. If you either Killdisk'ed your drive or smashed it, we have something to worry about :lolflag:

---

