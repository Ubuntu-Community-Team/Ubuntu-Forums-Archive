---
title: "Write permissions to mounted HDDs"
date: 2005-05-17
forum: Absolute Beginner Talk
---

### Post by zaxer on 2005-05-17
Hello guys.

How can I give writing permissions to mounted hdds?

Thanks guys  :)

---

### Post by dave9191 on 2005-05-17
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs) 

There are examples of how to do it for FAT32 and NTFS partions. You can read up the man pages for the mount command for more info (man mount). 

Dave

---

### Post by shof2k on 2005-05-17
Writing to FAT32 is fine, but writing using the builtin NTFS driver is either not possible or extremely risky.  I wouldn't recommend it.  There is captive-ntfs which is more stable, but requires 2 files (the MS ntfs driver imof) to work.  It's available via a google.

Hope this helps.

---

### Post by zaxer on 2005-05-17
Sorry guys but I cant manage your information.

Can anyone help me in a more begginer way?

Thanks guys.

---

### Post by Xian on 2005-05-17
[QUOTE=zaxer]Can anyone help me in a more begginer way?[/QUOTE]
If it's a Linux mounted partition then you can just do this in a terminal:

```
$ sudo mount -o remount,rw /dev/hdxz
```

Where x=the partition letter and z=the partition number.
So if you want to get write permissions to /dev/hda4 which is already mouted:

```
$ sudo mount -o remount,rw /dev/hda4
```

---

### Post by zaxer on 2005-05-17
[QUOTE=Xian]If it's a Linux mounted partition then you can just do this in a terminal:

```
$ sudo mount -o remount,rw /dev/hdxz
```

Where x=the partition letter and z=the partition number.
So if you want to get write permissions to /dev/hda4 which is already mouted:

```
$ sudo mount -o remount,rw /dev/hda4
```[/QUOTE]
 Its a windows partition..

---

### Post by Xian on 2005-05-17
[QUOTE=zaxer]Its a windows partition..[/QUOTE]
Then you'll need to do as dave9191 illustrated in the link:

To mount Windows partition:
* *Assuming that /dev/hda1 is the location of Windows partition (FAT)*

```
$ sudo mkdir /media/windows
$ sudo mount /dev/hda1 /media/windows/ -t vfat -o umask=000
```

To unmount Windows partition 

```
$ sudo umount /media/windows/
```

---

### Post by zaxer on 2005-05-18
Hi guys.

I got this message when trying to mount.

```

~$ sudo mount /dev/hda5 /mnt/Data -t vfat -o umask=000
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by Jussi Kukkonen on 2005-05-18
Hi zaxer,

I believe just gave you a link to the specific questions in Ubuntuguide ([http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)) in another thread, but if you still have problems, please post the result of
```
sudo fdisk -l /dev/hda
```

Also, please check that */mnt/Data* exists.

---

### Post by JimmyBEng on 2005-05-18
probably means that it isn't a FAT partition that you are trying to mount. Meaning that it must be NTFS, and like shof2k said above, writing to NTFS partions just doesn't work well.

EDIT: posting the results of fdisk -l will answer this for sure.

---

### Post by zaxer on 2005-05-18
[QUOTE=Jussi Kukkonen]Hi zaxer,

I believe just gave you a link to the specific questions in Ubuntuguide ([http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)) in another thread, but if you still have problems, please post the result of
```
sudo fdisk -l /dev/hda
```

Also, please check that */mnt/Data* exists.[/QUOTE]
 Here it is the result, and yes /mnt/Data does exist.

```

Disco /dev/hda: 40.0 GB, 40007761920 bytes
255 cabezas, 63 sectores/pista, 4864 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        4864    28828642+   f  W95 Ext'd (LBA)
/dev/hda5            1276        3707    19535008+   7  HPFS/NTFS
/dev/hda6            3708        4864     9293571   83  Linux


```

---

### Post by Jussi Kukkonen on 2005-05-18
And hda5 was the one you'd like to mount?

Sorry, but it looks like you're out of luck: the partition looks like it's NTFS, and like someone already said, you can't mount those read/write.

---

### Post by Xian on 2005-05-18
Yeah, best option in your case would likely be to create a FAT partition for data that both Windows and Linux can access with write permissions.

---

### Post by dave9191 on 2005-05-19
What about installing the windows driver for read/write for ntfs? Ive not done this myself, or seen any guides, but Ive heard people who've done this. If someone has the link for him...

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=dave9191]What about installing the windows driver for read/write for ntfs? [/QUOTE]

Very very very very very bad idea. The NTFS drivers that allow writing are unstable. Using them can destroy ALL OF THE DATA ON THE DRIVE!!!!!

The only way Ubuntu and Windows can write to the same drive safely is if the drive is formated as FAT32.

---

### Post by zaxer on 2005-05-19
Hi guys.

Thanks for your answers.

And yes, its hda5 the partition I want to mount and It looks like It is a NFTS one :( 
Like someone said before Im out of luck...

I remember a year ago when I used Knoppix I had a little software to move files from linux partitions to windows one, but don have a clue about its name...

Anyone remembers?


Thanks again guys. Your help makes me know a little more about Linux everyday :)

---

### Post by zaxer on 2005-05-24
Any info guys?

Please help!!

Thanks guys :)

---

### Post by animesh on 2005-05-24
you can change your ntfs  to fat32 with the help of partition magic in windows that may help you out it worked for me

---

### Post by Jussi Kukkonen on 2005-05-24
[QUOTE=zaxer]Hi guys.
I remember a year ago when I used Knoppix I had a little software to move files from linux partitions to windows one, but don have a clue about its name...

Anyone remembers?
[/QUOTE]

Well, as has been said, on Linux you can write to windows partitions without any special programs (just not to NTFS partitions).

Windows can also be made to read some Linux file systems, but you'll need a correct driver. Try googling "<fs-name> windows driver" or something. This will probably work if your file system is ext2 or ext3.

---

### Post by zaxer on 2005-05-25
Hi guys.

I finally did what you tell me. I converted my hda5 to FAT32.

I changed fstab so as to automatically mount that partition on boot, but it does not show in computer:/// while hda1 shows right.

Did I edit t hda5 line wrong or something?

Thanks.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1	/mnt/Windows	ntfs	user,ro,noatime,umask=000 0 0
/dev/hda5       /mnt/Data	vfat    umask=000       0       0

```

---

### Post by ZeroXsk8brdr on 2005-07-17
you might want to try adding in 'user' and 'rw' to the options (without quotes of course).

that's what i did.

---

