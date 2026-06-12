---
title: "fstab error"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by hellomoto on 2008-04-05
Trying to mount my media drive but get the following error:

```

mark@mark-desktop:~$ sudo mount -a
[mntent]: line 11 in /etc/fstab is bad

```

My fstab file:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=02eea92b-1a10-4d4a-81c5-09b7d7f55447 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=40bbaa97-5afc-45c3-9310-59897280f465 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#/dev/fd0	/media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb0   	/media/Media Drive   ntfs user,defaults     0        2

```


sudo lshw -C disk
```

  *-disk:1
       description: SCSI Disk
       product: WDC WD4000AAJB-0
       vendor: ATA
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 07.0
       serial: WD-WCAPW3010129
       size: 372GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5

```


any help please?
ty

---

### Post by SOULRiDER on 2008-04-05
You cant have a sdb0 partition. The number is something else. Please paste the output of this command:
```
sudo fdisk -l
```

Also, theres an error in
> /media/Media Drive 
I think you probably means a directory called "Media Drive". If you want to call it that you will need to change it to
> /media/Media\ Drivethat will make it appear as "Media Drive"

---

### Post by sisco311 on 2008-04-05
> /dev/sdb0       ***/media/Media Drive***   ntfs user,defaults     0        2-->
> /dev/sdb0       ***/media/Media\040Drive***   ntfs user,defaults     0        2\040 = ascii code of the space character

---

### Post by hellomoto on 2008-04-05
i changed to:

```

/dev/sdb   	/media/Media/040Drive   ntfs user,defaults     0        2

```

and now I get the following error:

```

NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
mark@mark-desktop:~$ 

```

getting closer though! ty for your help so far.

---

### Post by SOULRiDER on 2008-04-05
Please, post the output of
```
fsdik -l
```

Also, i think you mean
> /media/Media\040Drive

---

### Post by hellomoto on 2008-04-05
Ok solved that bit fstab now 

```

/dev/sdb1   	/media/Media\Drive   ntfs user,defaults     0        2

```

Now get this error:

```

mark@mark-desktop:~$ sudo mount -a
fuse: failed to access mountpoint /media/Media\Drive: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdb1 (Media Drive)

```

```

mark@mark-desktop:~$ sudo fsdik -l
sudo: fsdik: command not found

```

---

### Post by SOULRiDER on 2008-04-05
That may not be the partition. Please, paste the output of
```
sudo fdisk -l
```

---

### Post by hellomoto on 2008-04-05
have to go to work now :( (dont work in A&E!)

 but will try any surgestions you have tomoro morning. Ty for your help

---

### Post by astraljava on 2008-04-05
I believe you wanted to escape a space with backslash, not the letter 'D'. Please add it in between, and try again. :)

---

### Post by hellomoto on 2008-04-05
Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4af0f857

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    7  HPFS/NTFS
mark@mark-desktop:~$

---

### Post by hellomoto on 2008-04-05
```


mark@mark-desktop:~$ sudo mount -a
mount: mount point /media/Media\Drive does not exist
mark@mark-desktop:~$ mkdir  /media/Media\Drive
mkdir: cannot create directory `/media/MediaDrive': File exists
mark@mark-desktop:~$ sudo mount -a
mount: mount point /media/Media\Drive does not exist


```

---

### Post by hellomoto on 2008-04-06
all sorted mounts every time automatically.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=02eea92b-1a10-4d4a-81c5-09b7d7f55447 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=40bbaa97-5afc-45c3-9310-59897280f465 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#/dev/fd0	/media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1   	/home/mark/media   ntfs rw,user,auto    0        2

```

Thank you for you help

---

### Post by SOULRiDER on 2008-04-06
The problem you were having was because of the space in "Media Disk", im not sure how to specify theres a space there, but it should be comething like "Media\ Disk".

Anyways, please, markt he thread as solved from the Thread Tools menu on the top of the page.

---

