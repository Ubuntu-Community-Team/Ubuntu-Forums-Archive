---
title: "missing data"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by kiterguy on 2007-08-05
hey all

I have recently set up an external drive to store all of my data on.  I have partitioned it into three separate drives and have loaded my pictures on one of the drives.  I have accessed the pictures on this drive previously and I can access the other data on the other 2 drives. 

My problem is this:  I went to look at some pictures I had stored on my drive but I can not access the folders they are stored in.  I can see the folder names but the icons are no longer folders, and when I  Iook at the properties for one "folder" it says that it is an unknown type under "Type".  I can also not open or copy/paste or move these files that used to be folders full of pictures.

Please help as this was meant to be my back up of over 8 years of pictures.

Thanks

---

### Post by shadowen2 on 2007-08-06
Just wondering if you've checked the permissions on the folders?  Try to right click and then choose "Properties" then "Permissions" and make sure that they say "Read and Write"

---

### Post by kiterguy on 2007-08-06
yep tried that, but it comes back with a message saying permissions could not be determined?!

---

### Post by PandaGoat on 2007-08-06
How are you mounting the hard drive? Post your /etc/fstab file.

---

### Post by alienexplorers on 2007-08-06
Sounds like the drive is not being mounted.  Try PandaGoat's suggestion to display your fstab file.  Without the drive being mounted you will not be able to view anything on it.

---

### Post by kiterguy on 2007-08-08
Thanks for the help thus far guys!!  here is the print out from /etc/fstab/

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aa307190-df25-47ae-a2fc-61e98b254610 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b2f55a14-93c5-4aed-9aca-98b1cffa10a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by kiterguy on 2007-08-08
quick additional Q... why would I be able to see the files/folders in other partitions on the same drive as the one I can't see?

I'm only new so am still learning!

---

