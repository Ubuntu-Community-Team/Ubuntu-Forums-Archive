---
title: "Auto mounting an external USB HDD"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by showgun1 on 2007-07-04
Hey guys, this is a total newb question... 

I just installed Ubuntu a couple of weeks ago, and at the time, I was having a couple issues with partitioning, so ended up unplugging my external USB HDD (to make sure I wasn't installing onto it), Anyway, now when I boot up, it doesn't mount. If I unplug it and plug it back in, it mounts just fine. 

Can someone walk me though how to  fix it so I don't have to do that every time I boot up? I've done a search, and can't seem to find anything that addresses this specifically.

Thanks in advance.

---

### Post by Computer-Slave on 2007-07-05
> **showgun1 said:**
> Hey guys, this is a total newb question... 

I just installed Ubuntu a couple of weeks ago, and at the time, I was having a couple issues with partitioning, so ended up unplugging my external USB HDD (to make sure I wasn't installing onto it), Anyway, now when I boot up, it doesn't mount. If I unplug it and plug it back in, it mounts just fine. 

Can someone walk me though how to  fix it so I don't have to do that every time I boot up? I've done a search, and can't seem to find anything that addresses this specifically.

Thanks in advance.
I exactly don't know how to do it but u might need to edit your /etc/fstab file.

---

### Post by Nythain on 2007-07-05
find the device name of the usb hard drive:
plug it in, let it mount, in console type
```

sudo fdisk -l

```
then create a place where you want it to automatically mount... something like
```

sudo mkdir /media/usbdrive

```
can be anywhere really...
then edit your fstab
```

gksudo gedit /etc/fstab

```
and add a line something like this
```

/dev/sdxy    /media/usbdrive    ext3    defaults   0    2

```
make sure to change /dev/sdxy to whatever the device name of the usb drive is, make sure teh /media/usbdrive is whatever folder you made to mount it at, and make sure ext3 is actually whatever filesystem the drive is formatted in, either ext2, ext3, vfat, ntfs, ntfs-3g (if you have that package installed, it gives you write access to ntfs partitions), the list goes on... defaults should be good, but you can google "fstab options" to get more in depth on all the fstab options available... 0   2 is a nice setting... the 0 has something to do with dump blah blah blah (i have never really set it to anything other than 0 so i dont know exactly what it does) and the 2 is on how many mounts it will fsck i believe.

hope that helped... any questions, comments or problems just let us know

---

### Post by showgun1 on 2007-07-06
thanks for the help, but it doesn't seem to have done much. I've added the line to fstab, but when I boot in, it doesn't do anything

If i run fdisk -l I get the following:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       25738   206740453+   c  W95 FAT32 (LBA)


if I run a "sudo mount /dev/sdb1", the drive mounts ok, but I still have to run it manually.


the line I added to fstab was 
/dev/sdb1       /media/mediadrive  vfat	  defaults  0       2

Any suggestions?

---

### Post by aquavitae on 2007-07-06
After the word 'defaults' add ',auto':
/dev/sdb1 /media/media/drive vfat defaults,auto 0 2

Another option I usually add to that list is 'users'.  It sometimes sorts out access permission errors, but if you have any problems with permissions I'm sure we can give more suggestions.

---

### Post by Inxsible on 2007-07-06
or you can simply use pmount for all external devices. pmount will mount your drive under /media. and automount everytime you connect it. You also do not need any fstab entries for it.

```
sudo aptitude install pmount
``` ```
sudo pmount /dev/<device name> /MOUNT_POINT
```
MOUNT_POINT can be any name of your choosing. Make sure you dont use an existing name under /media since pmount actually creates the folder for you.



Hope that helps

---

### Post by ELR on 2007-07-06
This help me - [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

---

