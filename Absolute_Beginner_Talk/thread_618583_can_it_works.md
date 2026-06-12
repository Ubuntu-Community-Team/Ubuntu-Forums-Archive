---
title: "can it works???"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by '888' on 2007-11-20
i have hardisk with 2 linux operating system inside
first partition is for my gutsy gibbon 64 bit and the other for my gutsy gibbon 32 bit
but i have some problem....
my partition size for 64 bit is limited....
and i want to expand it...
what happen to my 64 bit if i format the 32 bit
and expand the partition area for 64 bit??
can it works without losing my data???

---

### Post by master_kernel on 2007-11-20
> **'888' said:**
> i have hardisk with 2 linux operating system inside
first partition is for my gutsy gibbon 64 bit and the other for my gutsy gibbon 32 bit
but i have some problem....
my partition size for 64 bit is limited....
and i want to expand it...
what happen to my 64 bit if i format the 32 bit
and expand the partition area for 64 bit??
can it works without losing my data???
It should, but obviously you would lose the 32-bit stuff. I advise backing up important files to a flash drive before continuing.

---

### Post by Skefflock on 2007-11-20
I think you can. Are you going to physically expand "/" for your first system? And you'll then need to edit /etc/fstab and remove the line with previous partition from there. So the system not to try to mount it every time. But it shouldn't corrupt your data anyway.

---

### Post by Inxsible on 2007-11-20
If your 32 bit partition lies before the 64 bit partition on the hard drive, then you will have to use [GParted Live CD]("http://gparted-livecd.tuxfamily.org/download.php") and move the start of the 64 bit partition. 

AFAIK, until Feisty, the GParted that came with The Live CD would not allow moving the start of any partition unless you formatted it and merged it meaning you lose all data.

---

### Post by '888' on 2007-11-20
if i erase my 32 bit
then using 64 bit live CD to edit partition for my 64 bit and expand it
should i edit /etc/fstab???
or ubuntu will renew those file???

---

