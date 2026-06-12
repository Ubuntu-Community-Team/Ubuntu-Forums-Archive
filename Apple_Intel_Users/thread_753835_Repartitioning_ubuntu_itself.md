---
title: "Repartitioning ubuntu itself ?"
date: 2008-04-13
forum: Apple Intel Users
---

### Post by Q_Ubunutu on 2008-04-13
Ive installed ubuntu. But i need to make a partition free for WinXP.

Im curious if someone had any idea how to do this without reinstalling ubuntu.

Somthing like bootcamp in Mac os x. but then for ubuntu ?

---

### Post by cyberdork33 on 2008-04-13
you can try to shrink the Ubuntu partition with gparted on the Ubuntu Live CD.

---

### Post by Q_Ubunutu on 2008-04-13
And how do i do that ? ( could you explain it to me like im a five year old? ) :confused:

---

### Post by essexboyracer on 2008-04-13
I found this tutorial real good, [http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php](http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php) it goes on to show you how to image the hard drive (make a snapshot copy, a bit like windows restore points.)

---

### Post by mrsteveman1 on 2008-04-13
Gparted will work, just dont actually MOVE any of the partitions, because that really screws with some operating systems bootloaders.

---

### Post by cyberdork33 on 2008-04-13
boot from the live cd and start the "partition editor" which is really gparted. It is pretty simple to figure out, no explanation needed.

---

