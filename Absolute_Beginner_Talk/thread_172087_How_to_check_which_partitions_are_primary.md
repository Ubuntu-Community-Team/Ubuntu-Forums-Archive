---
title: "How to check which partitions are primary?"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by minghai on 2006-05-07
Hi all,

    I orginally had WinXP installed on my machine, I then installed Ubuntu 6.06 beta 2 so I could dual boot.  Just out of curiosity, how do I find out which partitions are set as primary and if they are not, how to set them as primary?  My plan is to create a new partition (about 1GB), set it as primary and extract future Ubuntu isos there so I can install from that partition as though it was a CD.  Thank you.

Ming Hai

---

### Post by nanotube on 2006-05-08
to see your partitions from commandline, try
```
sudo fdisk -l
```
if you want a gui tool, install gparted:
```
sudo apt-get install gparted
```

---

### Post by minghai on 2006-05-08
I tried GParted but it doesn't show if a partition is primary or not.  Thanks.

Ming Hai

---

### Post by skippy81 on 2006-05-08
Try downloading qtparted from synaptic.  Its kinda like partition magic, much more powerful than the crappy gnome gui.  Right click on a partiton and select properties and you will see if its primary or logical.

---

