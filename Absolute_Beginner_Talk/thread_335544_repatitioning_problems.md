---
title: "repatitioning problems"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by Mba7eth on 2007-01-10
Hi everybody !!! 
I have installed ubuntu on my laptop 2 weeks ago. and i reserved the whole space for it. and choosed to have only 2 partitions ( /  and swap). Now i want to go repatrition the / directory. I have tryed parted but it says i most unmount the partition first. and it's my only partition. So is there a way to repartition this only partition ?????? 


Cheers, 
 Mba7eth

---

### Post by jvc26 on 2007-01-10
You cant repartition from within the drive (obviously) as that means you're messing with the filesystem and the resources it uses while it is running. Hence you need to run Gparted from either the Ubuntu LiveCd or from here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) Then run that cd, boot up and then do your partitioning from there and it should be ok :)
Il

---

### Post by bodhi.zazen on 2007-01-10
It is easiest to re-partition from a live CD.

Use either the Ubuntu CD or boot to the gparted CD.

You will likely need to edit both /boot/grub/menu.lst and /etc/fstab after you re-partition.

See these links for some guidance.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

[http://www.ubuntuforums.org/showthread.php?&t=316237](http://www.ubuntuforums.org/showthread.php?&t=316237)

You may ind it easier to re-install, but you would not learn as much that way !

GParted:

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by carlosfocker on 2007-01-10
Did you partition the drive as an LVM?  If so then you can shrink your existing partition and create another one. If not you are going to need to reinstall Ubuntu

---

### Post by Mba7eth on 2007-01-10
Sorry carlosfoker but what is LVM ??? 
and how can i know if my partition is an already LVM ?????????/


Cheers, 
Mba7eth

---

### Post by jvc26 on 2007-01-10
> **carlosfocker said:**
> Did you partition the drive as an LVM?  If so then you can shrink your existing partition and create another one. If not you are going to need to reinstall Ubuntu

You dont need to reinstall to change the size of a partition - the two sets of links from bodhi and from myself give you the stuff you need to change it without installing the entirety of ubuntu again.
Il

---

### Post by Mba7eth on 2007-01-10
Thanx alot guys :) 


Mba7eth

---

### Post by carlosfocker on 2007-01-10
> **Illuvator said:**
> You dont need to reinstall to change the size of a partition - the two sets of links from bodhi and from myself give you the stuff you need to change it without installing the entirety of ubuntu again.
Il

srry I posted just after you did.  Thats a good guide.

---

