---
title: "Help partitioning hard drive"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-03-03
I am doing a fresh install of edgy. My first install was my first time using linux. I finally managed to break it. I would like to create a seperate partition for my /home to live just in case. I have 250gb hard drive. I have 50gb for my /home. I have never ran with this type of setup.I am writing this from the live cd right now while looking at the new partitions. Does the /home partition need to be an extended or primary partition? Also, I assume they both need to be ext3?

---

### Post by Kateikyoushi on 2007-03-03
You can make home primary or extended as you like, filesystem is also not set just make sure it is not an MS filesystem, but I would stick with ext3 anyway.

This install will be almost the same as the previous except set /home as mount point for the partition you want to use as home, the rest can go as before, but now you can make / smaller more than 10GB would be a waste.

---

### Post by 67GTA on 2007-03-03
I am used to windows hogging the disc. I do not use windows anymore. I will only have Ubuntu on this machine. Never thought about all the extra space! I think the seperate home partition will come in handy. Thanks for the info, I was sitting here ready to hit the button as soon as someone cleared that up!

---

### Post by Kateikyoushi on 2007-03-03
There is no point in worrying about the partition size you can resize it anytime later from the cd.

---

