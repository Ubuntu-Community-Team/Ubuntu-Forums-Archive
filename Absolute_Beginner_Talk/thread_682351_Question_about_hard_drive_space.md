---
title: "Question about hard drive space"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Teh-Shewz on 2008-01-29
im sorry that this isnt totaly about ubuntu.
but.....
i have 30 gbs for ubuntu
and i have 100 for vista....witch i dont want
i shrunk vista down to 30 and i have 70 free.
and in vista i cant add that free space to ubuntu's partition
do i need to add it through ubuntu?
do i need to format the unsued space?
thanks for teh help.

i

---

### Post by mikewhatever on 2008-01-29
"do i need to add it through ubuntu?" Yes, sort of. Check out [GParted Live CD.]("http://gparted.sourceforge.net/livecd.php")
"do i need to format the unused space?" Yes, you do. The default format for Linux would be ext3 and it should get formated during the enlargement of Ubuntu partition, but I would go with an extra storage partition instead.

---

### Post by smartboyathome on 2008-01-29
Just start up the ubuntu livecd, and when it boots go to system > administration > partition editor, and double click on the partition ubuntu is currently on. You can give the extra space to Ubuntu here.

---

### Post by smartboyathome on 2008-01-29
> **mikewhatever said:**
> "do i need to add it through ubuntu?" Yes, sort of. Check out [GParted Live CD.]("http://gparted.sourceforge.net/livecd.php")
"do i need to format the unsued space?" Yes, you do. The default format for Linux would be ext3.

Technically, you just need to add the space to the other partition.

---

### Post by Teh-Shewz on 2008-01-29
Thanks guys.

---

