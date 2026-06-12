---
title: "accessing linux volume from windows machine"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by chymo on 2006-08-27
I have a ubuntu installed on a drive that also has xp on another partion.  This box also has a few other ntfs drives.  I am currently able to view these ntfs drives through another windows box on my lan (I have samba configured), but I need to read the linux volume to share some files to the windows box.  any ideas?

---

### Post by Tarvok on 2006-08-27
Assuming you are using ext3 for your filesystem (as opposed to reiser), [check this out]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm").

---

### Post by Ziox on 2006-08-27
> **chymo said:**
> I have a ubuntu installed on a drive that also has xp on another partion.  This box also has a few other ntfs drives.  I am currently able to view these ntfs drives through another windows box on my lan (I have samba configured), but I need to read the linux volume to share some files to the windows box.  any ideas?

Windows do not natively support reading or writing of ext3/2. You need to install ( [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html) ) that to allow windows to see the linux volume...though I'm not familiar with samba, but I think it should work.

---

### Post by seshomaru samma on 2006-08-27
maybe [this]("http://www.fs-driver.org/")?

---

### Post by chymo on 2006-08-27
I tried the above and not quite there... heres what I get...  On the windows box, I see \\linuxbox\MyFiles and this lists:

cdrom
cdrom0
hdc1
hdd1
hde1

those three drives are ntfs partitions and all of this is exactly the same as whats listed in my /media folder on the ubuntu box.  

I'm thinking I need to add the /. folder to my /media folder and it will work...  thoughts?

---

### Post by Shadyman on 2006-08-28
If you try the driver from [http://www.fs-driver.org/](http://www.fs-driver.org/)... You need to go to Control Panel, set the drive letter for the drive/partition you want, then you should be able to browse it from that drive letter.

---

