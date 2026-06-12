---
title: "help i can't change permisions for hard disks"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by singetak on 2006-08-27
how can i change the permision for other users for my hard disks
which say to me they are only readonly systems


dr-xr-x---  1 root      plugdev    8192 Aug 27 14:43 hda2
dr-xr-x---  1 root      plugdev    4096 Aug 24 18:59 hda5

](*,)

---

### Post by daou on 2006-08-27
You need to edit your fstab file

here is a good link: [http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

To open the file for editing use

sudo gedit /etc/fstab

in Ubuntu.

---

### Post by Kobalt on 2006-08-27
Hi,

What kind of hard disk is this : formated in, ext2 or 3, FAT32 or NTFS ? 
If it is a NTFS drive, you can't actually write it under Ubuntu, you'll need to install some stuff to do so. 

Cheerios !

---

### Post by MaximB on 2006-08-27
if you _**don't**_ have NTFS try in the terminal :
gksudo nautilus
now you should have the right premmisions to change ANY directory and hard-disk (again not NTFS).

---

### Post by singetak on 2006-08-27
Thanks MAXDDARK,Kobal,tdaou but i have ntfs hardisk 
what stuff i need to change:-k

---

### Post by daou on 2006-08-27
You cannot natively write from Ubuntu to an NTFS partition.

There is a way around, but **THIS COULD CORRUPT YOUR NTFS PARTITION**. That said, look here for help: [http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")

---

### Post by Kobalt on 2006-08-27
There are several ways to be able to write on your NTFS drive, but here is the one I use, the one I think is the easiest and the more efficient.
[HowTo install ntfs-3g]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g")

Cheerios !

---

### Post by singetak on 2006-08-27
thanks alot you guys
but i will not risk using ntfs-3g
i prefare partitioning my hardisk with a fat32
:-D

---

### Post by daou on 2006-08-27
When I said it could, it meant that there is a very small chance. But fat32 is always safer, it's how I got my rig set up. Or you could just install ext3 plugins for Windows, that is no problem.

---

### Post by singetak on 2006-08-28
i changed to fat32
but still the user that i enter desktop have no permision on it](*,) 
the only i can write to my hard disk is 
by alt-f2  then writing gksudo nautilus

---

### Post by singetak on 2006-08-28
i changed to fat32
but still the user that i enter desktop have no permision on it](*,) 
the only i can write to my hard disk is 
by alt-f2  then writing gksudo nautilus


this is my fstab:..
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5  	vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by kinematic on 2006-08-28
does user,exec,rw,auto work with fat32?....i'm asking because i've never dual booted with windows.
but i do know that fat32 and ntfs don't store permissions in the filesystem like linux filesystems do.

---

### Post by daou on 2006-08-31
You fstab vfat entry looks exactly like mine and I don't have a problem with access. It must be another problem with your user accounts and permissions.

---

