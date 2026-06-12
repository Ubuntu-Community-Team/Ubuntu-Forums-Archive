---
title: "File Access Errors"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by pmcastillo on 2007-01-05
I tried to access my 19GB NTFS drive and this is the message:

error: device /dev/hda2/ is not removable
error: could not execute pmount

Also, I tried to access my 8GB FAT32 drive and this is the message:

error: device /dev/hda1/ is not removable
error: could not execute pmount

How can I access my files?

---

### Post by jvc26 on 2007-01-05
When do you get those errors? Have you got the two drives mounted?
Il

---

### Post by pmcastillo on 2007-01-05
Ummmmm... I hope you can get my story T_T

Before I installed Ubuntu... 

I only got 1 harddrive with 2 partitions

C: 19GB NTFS (This is where my WinXP)
D: 19GB FAT32 (This is where my data files)

Then I installed Ubuntu 6.06, with Automatic Partitioning / Resizing...
And then I tried to open up the File Manager of Ubuntu, then I saw my drives...
The 19GB, and the 8GB... Then I tried to "double-click" it to access my files...

And there are those error messages... T_T

---

### Post by pmcastillo on 2007-01-06
mmmm... 1 got 2 screenshots here... maybe this could help

I got 1 harddisk with 2 partitions, (NTFS, and FAT32)

This is my 19.2GB NTFS partition...

[center]
[[IMG]http://img72.imageshack.us/img72/2044/screenshot1tk3.png[/IMG]](http://img72.imageshack.us/my.php?image=screenshot1tk3.png)
[/center]

This is my 9.3GB FAT32 partition...

[center]
[[IMG]http://img72.imageshack.us/img72/5264/screenshot2mj8.png[/IMG]](http://img72.imageshack.us/my.php?image=screenshot2mj8.png)
[/center]

I don't know what to do... ](*,)

---

### Post by pmcastillo on 2007-01-06
Here's my file structure... (I used [http://www.fs-driver.org/](http://www.fs-driver.org/))

[center]
[[IMG]http://img72.imageshack.us/img72/8108/2rn8.jpg[/IMG]](http://img72.imageshack.us/my.php?image=2rn8.jpg)
[/center]

---

### Post by notepad on 2007-01-06
you should show us the contents of your /etc/fstab

---

### Post by pmcastillo on 2007-01-06
Ummmm... here:


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0 
```

---

### Post by notepad on 2007-01-16
you dont have fstab entries for hda1 and hda2.

id like to know the result of 
ls -al /media

if you can post that for me. ill reply with suggested entries for these partitions in your fstab.

---

