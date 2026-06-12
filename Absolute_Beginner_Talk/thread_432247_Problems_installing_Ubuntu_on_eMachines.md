---
title: "Problems installing Ubuntu on eMachines"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by QuestM3/4 on 2007-05-03
Well my computer has been acting crappy lately so I decided to install Ubuntu and let it reformat the whole hard drive. I used the same disc I used for my PC at work which loaded flawlessly, but its not working here. It will get to about 86%, then the screen goes black and it ejects the disc. It will not reboot by itself or anything. When I turn it back on, it acts like its going to load, but then says GRUB loading...Error 15. I'm thinking the hard drive is not fully formatted for some reason. Is there someway I can format when I boot up from the live CD? Thanks.

---

### Post by mi_were on 2007-05-03
> **QuestM3/4 said:**
> Well my computer has been acting crappy lately so I decided to install Ubuntu and let it reformat the whole hard drive. I used the same disc I used for my PC at work which loaded flawlessly, but its not working here. It will get to about 86%, then the screen goes black and it ejects the disc. It will not reboot by itself or anything. When I turn it back on, it acts like its going to load, but then says GRUB loading...Error 15. I'm thinking the hard drive is not fully formatted for some reason. Is there someway I can format when I boot up from the live CD? Thanks.


I had a similar problem with my friend's emachine and by using the Alternate Ubuntu CD instead of the LiveCD I got a good install done.

As for formating I always fall back on bad habits and use my bootable dos CD!
"fdisk mbr" at the dos prompt should clear out the Master Boot Record after a good old format.

---

### Post by gn2 on 2007-05-03
> **QuestM3/4 said:**
>  Is there someway I can format when I boot up from the live CD? Thanks.

Perhaps you should try the Alternate CD?
.
You can format the partitions during the install process, or even delete the existing ones and create new ones.

---

### Post by QuestM3/4 on 2007-05-04
Thanks for the replies. I'll try the alternate disk then.

---

### Post by QuestM3/4 on 2007-05-10
Well while trying all sorts of stuff like using another hard drive, I noticed that the CPU fan would stop working after being turned on for a minute or so. I left the case opened and aimed a small fan towards the motherboard and tried installing Ubuntu then. Guess what, it installed completely with no errors and never crashed. I bought a new CPU fan yesterday, problem solved. Now I just need to get my Nvidia card, E-Mu sound card, and wireless USB thingy to work.:guitar:

---

