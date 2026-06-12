---
title: "Second Linux Drive"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2006-07-24
Just added a second drive to my linux box and I can;t get it to permanently mount it at bootup. I have to always goto System->Administration->Disks and manually mount it.


Drive is sdb1 and I want to mount it at /media/drive2 and has file type ext3



You can see my system information  [here]("http://scorpuk.plus.com/phpsysinfo/")


Tnx in advance for any help. :)

---

### Post by Kilz on 2006-07-24
> **Scorpuk said:**
> Just added a second drive to my linux box and I can;t get it to permanently mount it at bootup. I have to always goto System->Administration->Disks and manually mount it.


Drive is sdb1 and I want to mount it at /media/drive2 and has file type ext3



You can see my system information  [here]("http://scorpuk.plus.com/phpsysinfo/")


Tnx in advance for any help. :)
I think you will have to add it to your fstab file. Its the file that is a list of all the things auto mounted. You might want to use the line for the first drive as a guide.
```
gksudo gedit /etc/fstab
```

---

### Post by Scorpuk on 2006-07-24
yay

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /media/drive2   ext3    defaults,errors=remount-ro 0    

did as you said and added it in just like the 1st one and it worked a treat.

Had a little heart flutter when computer booted up and I got the following message:

> dev/sda1 has been mounted 30 times without being checked, check forced
{long slow check of drive}
dev/sdb1 has been mounted 30 times without being checked, check forced
{long slow check of drive}


I thought when I installed ubuntu it would have checked the drive at the time. :D 

now to reboot for 2nd time and see if everything is still ok :neutral:

---

### Post by Kilz on 2006-07-24
> **Scorpuk said:**
> yay

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /media/drive2   ext3    defaults,errors=remount-ro 0    

did as you said and added it in just like the 1st one and it worked a treat.

Had a little heart flutter when computer booted up and I got the following message:



I thought when I installed ubuntu it would have checked the drive at the time. :D 

now to reboot for 2nd time and see if everything is still ok :neutral:

The auto file system check runs every 30 boots. I think its a good thing because it stops errors before they get to big.

---

