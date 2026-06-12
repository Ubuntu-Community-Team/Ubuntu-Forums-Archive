---
title: "Problems accessing partitions"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2007-03-13
Brand new to Unix and having trouble with Ubuntu and being able to write data to my other partitions.  I have two WD 80Gb SATA drives, which i partitioned to in step 5 on the instillation choosing manually edit partition table: Drive 1, first 20 Gb is root (/dev/sda1), 2Gb is Swap (/dev/sda2) and the remainder is dedicated to programs(/dev/sda3).  Drive 2 i left as an 80Gb drive meant for storage (/dev/sdb1).  after Ubuntu is installed, i have tried to write data to either programs(/dev/sda3) or storage (/dev/sdb1) and it says that i do not have access to do so.  when i look under the permission tab it says only that the user root can access these drives.  what am i doing wrong.


Thank you
Jon

---

### Post by taurus on 2007-03-13
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by poordamnedfool on 2007-03-13
jqaskwig@poordamnedfool:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3dbff518-d814-40dc-88d9-3d530149086a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=d39419de-455b-467a-a516-ce744d4f67fe /media/sda3     ext3    defaults        0       2
# /dev/sdb1
UUID=c31899bb-a4d4-4422-8b34-6f7f7babfd2b /media/sdb1     ext3    defaults        0       2
# /dev/sda2
UUID=04d4aaed-9a38-48db-8a69-89d26ccf0b15 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2007-03-13
From a terminal, do

```
sudo chown -R jqaskwig:jqaskwig /media/sdb1
sudo chown -R jqaskwig:jqaskwig /media/sda3
ls -la /media
```
you should be able to write to both /media/sda1 & /media/sda3 since you are the proud owner of those partitions.

---

### Post by poordamnedfool on 2007-03-13
Thank you works great!

---

### Post by poordamnedfool on 2007-03-13
one more question how do i rename the drives.

---

### Post by Najand on 2007-03-13
Make Directories with the names you like in  /media, then go through fstab and edit the appropriate mountpoint in it to the direcotry name you made.

---

### Post by ububaba on 2007-04-10
> **taurus said:**
> From a terminal, do

```
sudo chown -R jqaskwig:jqaskwig /media/sdb1
sudo chown -R jqaskwig:jqaskwig /media/sda3
ls -la /media
```
you should be able to write to both /media/sda1 & /media/sda3 since you are the proud owner of those partitions.

taurus
I followed your instructions but somehow I am not able to create folders on 
drives [COLOR="DarkRed"]sda3 & sda4[/COLOR] despite being so proud. What next?
[HTML]bing@bong:~$ ls -la /media
total 32
drwxr-xr-x  8 root root 4096 2007-04-10 21:49 .
drwxr-xr-x 21 root root 4096 2007-04-10 20:28 ..
lrwxrwxrwx  1 root root    6 2007-04-10 19:45 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-04-10 19:45 cdrom0
lrwxrwxrwx  1 root root    7 2007-04-10 19:45 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-04-10 19:45 floppy0
drwxr-xr-x 21 root root 4096 2007-04-09 03:43 sda1
drwxr-xr-x  2 root root 4096 2007-04-10 21:48 sda2
drwxr-xr-x  2 bing bing 4096 2007-04-10 21:49 sda3
drwxr-xr-x  2 bing bing 4096 2007-04-10 21:49 sda4
[/HTML]

---

