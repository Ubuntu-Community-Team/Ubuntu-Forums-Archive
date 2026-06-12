---
title: "Format A Hardrive"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Aloush on 2008-04-02
Hey!
I have just plugged in a 30GB hardrive and i want to install windows through virtual box onto it but how can i format it first?

Thanks

---

### Post by Aloush on 2008-04-02
Please somebody i need to do this

---

### Post by Aloush on 2008-04-02
Anybody i am wanting XP now ?:D

---

### Post by annda on 2008-04-02
the easiest way i can think of formatting the drive to fat32 iis GParted:

system > administration > partition editor

---

### Post by Aloush on 2008-04-02
I dont have that option

---

### Post by fedex1993 on 2008-04-02
aloush please wait 24 hours to bump please

---

### Post by halitech on 2008-04-02
boot from a floppy that has the format command on it and format the drive that way

---

### Post by Whiffle on 2008-04-02
Are you intending to install windows so that it can be used through virtualbox? or so that you can boot off it?  If its through virtualbox, then this is what I'd do (in terminal):

dmesg
(look and see which drive it is, should be something like sda, sdb, sdc, etc.  I'll call it sdx)

sudo fdisk -l /dev/sdx

Does it already have partitions?  If not, you'll need to make some.
sudo fdisk /dev/sdx

(make partitions, its pretty self explanitory but ask if you need help)

sudo mkfs.ext3 /dev/sdx1
where 1 is the number of the partition.  This will make an ext3 filesystem.

Alternatively, you could use gparted for the partitioning and filesystem making.  

Thats should be it.

---

### Post by mike555 on 2008-04-02
You can just get " Gparted " , install it and it should let you format it ,  it's a good thing to have anyway , to format camera cards or CDRW's ......

---

### Post by Aloush on 2008-04-02
Thanks everybody

---

