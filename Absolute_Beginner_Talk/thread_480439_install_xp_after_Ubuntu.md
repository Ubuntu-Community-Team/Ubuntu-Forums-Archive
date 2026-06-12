---
title: "install xp after Ubuntu"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Kuriozu on 2007-06-21
I have ubuntu on a HD partitioned in half, how do I add windows xp on the same HD?

---

### Post by phr0ze on 2007-06-21
If you haven't done anything with ubuntu yet, its best just to install windows, let it overwrite ubuntu, then reinstall ubuntu.

---

### Post by zerobinary on 2007-06-21
no use knoppix there is a program call qparted resize the partition and format one for window lol

---

### Post by LaRoza on 2007-06-21
You could install XP to a different partition, however, you will not be able to boot Ubuntu without reinstalling Grub. If you want to resize the current partition, use GParted, in my sig. It is faster to download that an entire OS and it is more up-to-date. Using the Super Grub Disk, to install Grub, or use the Ubuntu disk.

---

### Post by Kuriozu on 2007-06-21
Yes this is what I want to do, but don't know how to install windows at his point. can you give me some tip on overwriting ubuntu please?

---

### Post by LaRoza on 2007-06-21
Use GParted to erase all the partitions, and then format the hard drive as one primary partition as NTFS. 

See my sig for GParted.

---

### Post by Kuriozu on 2007-06-21
Did the steps above, now I reboot using windows xp cd and I get " GRUB Loading, please wait..., error 22"

---

### Post by LaRoza on 2007-06-21
You are not booting from the cd if you are using Windows and you get a grub error. 

"error 22" means it can't find the booting os, if you uninstalled Ubuntu this is normal. 

To boot from a cd, either choose the cd drive as the booting device or reconfigure BIOS.

---

### Post by buuntuu! on 2007-06-21
hi kuriozu, 
what steps exactly did you take?

---

### Post by phr0ze on 2007-06-21
> **zerobinary said:**
> no use knoppix there is a program call qparted resize the partition and format one for window lol

He already had it partitioned, Windows can be unfriendly if its not on the first partition and it will definately screw up grub. Thats why I suggest just install windows, then install ubuntu. Doing it that way usually causes less headaches in the long run.

---

### Post by Kuriozu on 2007-06-21
Ok guys, I'm on it.  I had to remove grub and find a bootable disk, now I'm installing windows then I will follow what you sugested.

thanks to all

---

