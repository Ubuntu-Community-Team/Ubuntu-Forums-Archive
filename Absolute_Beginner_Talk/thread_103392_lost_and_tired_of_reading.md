---
title: "lost and tired of reading"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by RBH on 2005-12-14
i have never used anything but windows till about 2 hours ago. i will no doubt be totally frustrated for the next few weeks till i get used to this but in the mean time i am trying to get a few things to work. 

1. i have a local network of 4 other computers, all on windows xp using a linksys router. i cannot see those computers and of course they dont see me now. how do i configure this c to get on my home network?

2. i figure i know the answer but it doesnt hurt to ask. i have 2 other hard drives in this pc and they were formatted when i had xp on it. am i right in assuming now that i cant access these drives without reformatting them? right now i cant access the data on them and they dont even show. 

thanks for the help, and i am sure before it's done i will have been here for many hours reading.

---

### Post by Gandalf on 2005-12-14
1- try Places -> Network servers to see others, about being seen is a bit more complicated but look for samba on this forum or [http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)

2- of course not, you just need to alter /etc/fstab file, look at [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows) for more information

---

### Post by aysiu on 2005-12-14
[QUOTE=Gandalf]
2- of course not, you just need to alter /etc/fstab file, look at [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows) for more information[/QUOTE] Just as a P.S., the Ubuntu Guide assumes your Windows partitions are at /dev/hda1. If you want to be certain where they are and *what* they are (NTFS or FAT32), type this in a terminal ```
sudo fdisk -l
```

---

