---
title: "Can't read/write HD no permission"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by el mariachi on 2007-06-21
I just fresh-installed ubuntu. I have a 3 disk setup but only one is giving me a headache.

After the install the disc's owner is set to root and I can't neither read nor write... how can I change the permissions so that I'm the disc's owner?

---

### Post by ScottY_ on 2007-06-21
If it's an IDE drive then the drive itself may have some connectors (forgotten proper name) on the back with pins, they might need changing. Or the BIOS might have something to do with it, reboot and you will need to hit a key, it says on the BIOS boot screen, usually F2, F8, F12 or DEL, in the BIOS you might need to edit some settings

---

### Post by el mariachi on 2007-06-21
> **ScottY_ said:**
> If it's an IDE drive then the drive itself may have some connectors (forgotten proper name) on the back with pins, they might need changing. Or the BIOS might have something to do with it, reboot and you will need to hit a key, it says on the BIOS boot screen, usually F2, F8, F12 or DEL, in the BIOS you might need to edit some settings

Thanks, but no. They're all SATA drives

---

### Post by haricharan on 2007-06-21
are all the partitions mounted properly...print ur fstab and mstab..maybe we can help...
```
cat /etc/fstab
``````
cat /etc/mtab
```

---

### Post by Rocket2DMn on 2007-06-21
You can try
```
sudo chown -R *username* /path/to/mount/point
```
But it seems like it should let you in automatically.  Is the drive setup in /etc/fstab ?
Is the drive NTFS?

---

### Post by el mariachi on 2007-06-21
fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=dfae76c7-8d3c-4940-aa1c-3cbdb9be944b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc1
UUID=1209f023-5249-4552-97f7-688bb7c41b65 /home           ext3    defaults        0       2
# /dev/sda1
UUID=eaab5904-5936-46d3-880c-d1ff29ec5b91 /home/mariachi/cave ext3    defaults        0       2
# /dev/sdb3
UUID=659986bb-9485-4714-807d-3c44df913eb2 /usr            ext3    defaults        0       2
# /dev/sdb1
UUID=F2A4C829A4C7EE63 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb4
UUID=d9c40b5e-4f38-490f-bcf9-381335796bb8 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

mstab
```
mariachi@central-dogma:~$ cat /etc/mstab
cat: /etc/mstab: No such file or directory

```

---

### Post by el mariachi on 2007-06-21
> **Rocket2DMn said:**
> You can try
```
sudo chown -R *username* /path/to/mount/point
```But it seems like it should let you in automatically.  Is the drive setup in /etc/fstab ?
Is the drive NTFS?

no it's ext3
mount point is  /home/mariachi/cave

---

### Post by Rocket2DMn on 2007-06-21
```
fdisk -l
```

---

### Post by Thomar on 2007-06-21
Okay, it looks like you have a windows drive.  You're going to want to install the NTFS Configuration Tool (Applications>Add/Remove Programs), that will let anyone access the NTFS drive.

To change permissions, you're going to have to edit fstab and reboot (chown and chmod don't work on mounted drives).  I'm not quite sure how I fixed that, but I posted what I did in this thread:
[http://ubuntuforums.org/showthread.php?t=467116](http://ubuntuforums.org/showthread.php?t=467116)


You could also try pressing Alt-F2 and running "gksudo nautilus", that will let you open a window as root (very dangerous, you can mess up your file system if you change the wrong thing), and since root owns those drives you might be able to change their permissions.

---

### Post by Eldar11 on 2007-06-21
I have a similar problem with a Ubuntu drive, I have no idea what format it is, I havent had to look yet, but I cant read or write to it and it says the owner is root, how would i fix that?  would re-formatting it with gParted work? there is no data I want or need on that drive.

---

### Post by Rocket2DMn on 2007-06-21
> **Thomar said:**
> Okay, it looks like you have a windows drive.  You're going to want to install the NTFS Configuration Tool (Applications>Add/Remove Programs), that will let anyone access the NTFS drive.
.

It's not the windows drive that's the problem, it's an ext3 drive, the mount point is listed above.

Please post the output of
```
fdisk -l
``` so we can compare with the fstab file.

---

### Post by el mariachi on 2007-06-21
this is weird... it didn't output anything, but the command is right..
```
mariachi@central-dogma:~$ fdisk -l
mariachi@central-dogma:~$ fdisk /dev/sda

Unable to open /dev/sda
mariachi@central-dogma:~$ 

```

---

### Post by haricharan on 2007-06-21
sorry..typing mistake...that was mtab
```
cat /etc/mtab
``` 
it lists ur mounted partitions and the permissions with which its mounted....maybe that wud help.....

---

### Post by ronnybob on 2007-06-22
I just had the same problem what I did was I formatted the second HDD to FAT 32 then mounted the HDD and I can copy & paste anything I want but I am not able to change permissions from READ ONLY, to READ & WRITE, I don't care anyway as long as I can work with it.

---

### Post by pjkoczan on 2007-06-22
Check the permissions/ownership on the mount point. You can either chown it to yourself or give it mode 0777 (global read-write for the directory), depending on how you'd like to lock it down. I, for instance, have a scratch drive with the mount point owned by root with mode 0777. It works fine for me.

Also, check the permissions on the parent directories of the mount point as well. If one of those permissions are broken (you should have at least read and execute permissions), then you won't be able to get any lower in the directory tree.

As a side note, you'll have to either sudo or become root in order to mount or run fdisk or do other administrative tasks.

You might also want to consider setting the sticky bit to further protect files if this is a multi-user machine (chmod +t mountpoint). See [http://en.wikipedia.org/wiki/Sticky_bit](http://en.wikipedia.org/wiki/Sticky_bit) for more details.

---

### Post by el mariachi on 2007-06-30
chown mariachi /home/mariachi/cave worked for me;)

there's a lost+found folder (locked) in the hard drive, is it normal? also, how can I make my deleted files, from that disk, be sent to trash instead of .trash-cave inside the partition?

---

