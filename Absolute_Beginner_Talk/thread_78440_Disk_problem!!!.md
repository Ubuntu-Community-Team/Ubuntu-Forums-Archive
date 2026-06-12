---
title: "Disk problem!!!"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by UbuntuUbuntu7 on 2005-10-18
So i formatted my disk, and then i tried to start the computer up, but it was a little strange(i think i had the wrong values in etc/fstab)... anyway. I checked the new disk and finds this: [IMG]http://img180.imageshack.us/img180/2554/skrmdump5oh.png[/IMG] a folder that i cant touch("no permissions"), the disk is not empty, and i cant move anything to the disk("no permissions"). 

I wanna format it throughly. How?

Well, here is my /etc/fstab:

proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/disk     ext3    defaults	 0       0

Is that right? Otherwise, please, can someone tell me what to do? :???:

---

### Post by Murgle on 2005-10-18
what did you do to format the drive?  do you know what exact command you used?

---

### Post by UbuntuUbuntu7 on 2005-10-18
I used gparted. I hope formating is what it does. Now when i check the program again i did this: I first converted the ntfs disk to ext3... where i did get that from... i dont know. Maybe i thought that was like a format in linux language. 

Anyway... after that i deleted it. Then i choosed "new".... could this have destroyed the disk?

---

### Post by Murgle on 2005-10-18
I know that parted is a partition manager, for resizing and such I don't think that it can format but I could be wrong.  What you want to is cfdisk.  it is curses based so there is text only but it's still solid.  If anyone knows of a good graphical formatting program I would like to know.  Once you have formated with cfdisk then you should go back into gparted and make your partitions

---

