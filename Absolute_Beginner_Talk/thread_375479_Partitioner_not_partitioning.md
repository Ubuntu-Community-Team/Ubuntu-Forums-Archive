---
title: "Partitioner not partitioning"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by andrewlinn957 on 2007-03-03
Today i tried to install Edgy 6.10 on my comp using the alternate CD. manually editing the partition table, i tried to resize my windows partition from 294GB to 200GB. However. when i enter the new partition size and try to create the new partition all that happens is the prompt goes away for a few seconds, only for the main partition prompt to come back, not showing the new partition or any changes at all. I don't know whats going on, esp having done this before on my other (older) comp. 
thanks

---

### Post by taurus on 2007-03-03
Maybe you need to boot into Windows first and defrag the harddrive a few times before you try to resize it with the alternate CD.

---

### Post by steve101101 on 2007-03-03
> **taurus said:**
> Maybe you need to boot into Windows first and defrag the harddrive a few times before you try to resize it with the alternate CD.

I agree. The partitioner may not allow you to resize the drive it there are used bits all over the place.

---

### Post by andrewlinn957 on 2007-03-03
i defragged it a week ago, and on your advice 2 times in the last 30 minutes. Also, i checked the disk for errors and there were none. The same thing happened when i tried to partition

---

### Post by taurus on 2007-03-03
Maybe GParted LiveCD would work better since it comes with the latest version of GParted.  So, use it to resize your harddrive.  Then, boot from the alternate CD and see if you can install Ubuntu on that empty partition.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by andrewlinn957 on 2007-03-03
are there any windows based partition tools you'd reccommend as ive had problems with the liveCD before
thanks

---

### Post by taurus on 2007-03-03
But this is GParted LiveCD, not Ubuntu LiveCD.

---

### Post by andrewlinn957 on 2007-03-03
oh right cool, will do, after i get some sleep :D

---

### Post by Deviltongue on 2007-03-04
I'm having a similar problem... how would I defrag my harddrive?

---

### Post by andrewlinn957 on 2007-03-04
to defrag your HD (with windows) go to my computer ---> right click on whatever drive you want to defrag ---> goto properties ---> tools ---> defrag now

---

### Post by andrewlinn957 on 2007-03-06
G parted told me that there were errors on my HD and that i should run chkdisk, which i did, and now everythin is grand! 
First post from Ubuntu!

---

