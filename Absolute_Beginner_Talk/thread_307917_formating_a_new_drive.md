---
title: "formating a new drive"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by rumour88 on 2006-11-27
Hi Guys,

After finally getting Ubuntu up and running just the way I want it I have encountered a bit of a problem.

I tried to format a second hard drive (to a Fat32 partition with a gig swap) with GParted which appeared to work but the drive would not mount, but I've have had problems with GParted in the past so decided to try with cfdisk instead. This appeared to also work but the drive will still not mount and the partitions apper as unknown in GParted.

Does any one know why this would happen or how to fix it. Thanks for any help.

---

### Post by Bachstelze on 2006-11-27
GParted has always worked for me... What happens when you try to mount your partitions ?

---

### Post by rumour88 on 2006-11-27
Hi, yeah most of the time GParted works fine for me as well.

When I try to access the drive i get the error 
> Unable to mount the selected volume. mount: according to mtab, /dev/hdb1 is already mounted on /mount failed 
Which sort of makes sense as it has been configured in fstab to mount at boot although I did use just the same settings as hda for this, I dont know if this could be causing the problem.

Thanks.

---

