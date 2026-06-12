---
title: "Need to remount another partition to /usr partition"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by fer5437 on 2006-05-22
This is my /etc/fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /home           ext3    defaults        0       2
/dev/hdb2       /usr            ext3    defaults        0       2
/dev/hdb3       /var            ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



Then this is my sudo fdisk -l output
> 
Disk /dev/hda: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          91      730926   83  Linux
/dev/hda2              92         146      441787+  82  Linux swap / Solaris

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         243     1951866   83  Linux
/dev/hdb2             244         486     1951897+  83  Linux
/dev/hdb3             487         729     1951897+  83  Linux
/dev/hdb4             730        2434    13695412+   5  Extended
/dev/hdb5             730        1251     4192933+  83  Linux
/dev/hdb6            1252        1513     2104483+  83  Linux




Now my problem here is I try to mount /dev/hdb5 to /dev/hdb2. Do there any way to mount the 2 partition together because there only left 150MB space left in /dev/hdb2?[FONT="Arial"][/FONT]

---

### Post by Ecthelion on 2006-05-22
[QUOTE=fer5437]Now my problem here is I try to mount /dev/hdb5 to /dev/hdb2. Do there any way to mount the 2 partition together because there only left 150MB space left in /dev/hdb2?[/QUOTE]

I don't understand...
You cannot change /dev/hdb5 to hdb2 except if you are going to repartition everything...
/dev/hdb2 and /dev hdb5 are the names of the partitions and except by repartitioning you cannot change them.

So what do you exactly want?
I think you want to repartition your disk so that the partition hdb5 and hdb2 become 1 bigger partition.

You can use Gparted for that, or if it doesn't work, I would recommend qtparted.

Be sure to backup your data before repartitioning everything.
If you try qtparted i would also advice to
```
sudo umount -a
```
before you change anything, otherwise it's not safe.
After you use qtparted you can 
```
sudo mount -a
```
to use your disks again, and if they aren't all mount, just restart your computer and it should be alright.

---

### Post by Ecthelion on 2006-05-22
If you only wanted to change hdb2 to hdb5 and vice versa,
then all you had to do is change your fstab to this
>  # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb1 /home ext3 defaults 0 2
/dev/hdb**5** /usr ext3 defaults 0 2
/dev/hdb3 /var ext3 defaults 0 2
/dev/hda2 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
**/dev/hdb2 /media/old-usr ext3 defaults 0 0**



I added a line so that you could acces your old /usr.
Be aware that before mounting this you have to add a folder
```
sudo mkdir **/media/old-usr**
```

Or to anywhere you would like to have that old-usr

---

### Post by fer5437 on 2006-05-22
when I try to umount -a, this is the output I get
> 
umount: /var: device is busy
umount: /usr: device is busy
umount: /home: device is busy
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy
fer@z-cg-fer:~$



Do I need to do it in recovery mode??

---

### Post by fer5437 on 2006-05-23
Make it simple, now my /usr partition is nearly full. I need to repartition it to have more space. So how can I do it since umount -a I get this output
> 
umount: /var: device is busy
umount: /usr: device is busy
umount: /home: device is busy
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy
fer@z-cg-fer:~$


I have gparted install in my machine. Please advise

---

### Post by Ecthelion on 2006-05-23
Hmm, if you get that "device is busy" all the time, then I would advice you to download and burn the Gparted live cd...
You can boot it and that would make sure that none of your disks are "busy"

---

