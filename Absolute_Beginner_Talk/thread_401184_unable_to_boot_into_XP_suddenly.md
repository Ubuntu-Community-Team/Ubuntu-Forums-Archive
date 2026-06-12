---
title: "unable to boot into XP suddenly"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by rmadhu on 2007-04-04
Suddenly I am unable to boot into my XP partitiion . When the boot loader comes up .. I am getting this error .
Error 13 .---

Please help as I am getting this error . I am able to boot into my Linux partition though .

Thanks,

---

### Post by BarfBag on 2007-04-04
What changes did you make before this started to happen?

---

### Post by rmadhu on 2007-04-04
only thing i can remember of is changing /etc/fstab file 
I modified the 
/dev/hda1       /media/hda1     vfat    defaults        0       0

to 
/dev/hda1       /media/hda1     vfat    rw,user,noauto         0       0

I have undone it .. Still I am unable to boot on to the partition

---

### Post by Kobalt on 2007-04-04
Did you access your windows partition with such things as Ntfs-3g ? Did you move/delete/create files on this win partition from Ubuntu ?

---

### Post by rmadhu on 2007-04-10
I think i copied one file from UBUNTU to WIndows .. thats the only thing I remember

---

