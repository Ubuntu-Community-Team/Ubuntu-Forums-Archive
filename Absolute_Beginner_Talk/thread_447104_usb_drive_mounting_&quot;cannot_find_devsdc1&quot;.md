---
title: "usb drive mounting &quot;cannot find /dev/sdc1&quot;"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-05-17
I have an external usb drive with 2 partitions. One is FAT32 and the the other is ETX2 (or 3).

I would like to mount the EXT2 partition under /media/storage, so I created the mount point.

The output of *sudo fdisk -l* is (relevant part only):
```
Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       26223   210636216   83  Linux
/dev/sdc2           26224       30401    33559785    b  W95 FAT32
```

In */etc/fstab* I entered:
```
/dev/sdc1 /media/storage auto users,noauto 0 0
```

When I attach the usb drive and try to mount it I get an error that */dev/sdc1* cannot be found.

Can anyone clear me up on what I have done wrong here? Also did I select the right attributes for the drive in */etc/fstab*?

Thanks!

---

### Post by taurus on 2007-05-17
What if

```
sudo mkdir /media/sdc1
sudo mount -t ext2 /dev/sdc1 /media/sdc1
df -h
```

---

### Post by PartisanEntity on 2007-05-17
I edited the command you posted like so:

```
sudo mount -t ext2 /dev/sdc1 /media/storage
```

This worked. What do I enter in /etc/fstab now?

---

### Post by taurus on 2007-05-17
Look at your original entry in /etc/fstab again.  If you look at it carefully, you probably would have guessed the typo.

```
/dev/**[COLOR="Blue"]sda1[/COLOR]** /media/storage auto users,noauto 0 0
```

Otherwise, add this line in your /etc/fstab instead (at the end).

```
/dev/sdc1   /media/storage   ext2   defaults   0   0
```

---

### Post by PartisanEntity on 2007-05-17
> **taurus said:**
> Look at your original entry in /etc/fstab again.  If you look at it carefully, you probably would have guessed the typo.

```
/dev/**[COLOR="Blue"]sda1[/COLOR]** /media/storage auto users,noauto 0 0
```

Otherwise, add this line in your /etc/fstab instead (at the end).

```
/dev/sdc1   /media/storage   ext2   defaults   0   0
```

Actually my typo was only here on the forum, I actually did enter /dev/sdc1 in /etc/fstab

---

### Post by PartisanEntity on 2007-05-17
```
/dev/sdc1   /media/storage   ext2   defaults   0   0
```

/dev/sdc1 did not mount when I entered the above into /etc/fstab

---

### Post by taurus on 2007-05-17
Output of 

```
sudo fdisk -l
df -h
```

---

### Post by PartisanEntity on 2007-05-17
sudo fdisk -l:
```
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3325    26708031    7  HPFS/NTFS
/dev/hda2            3326        7257    31583790   83  Linux
/dev/hda3           11800       12161     2907765    5  Extended
/dev/hda4            7258       11799    36483615    b  W95 FAT32
/dev/hda5           11800       12161     2907733+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       26223   210636216   83  Linux
/dev/sdc2           26224       30401    33559785    b  W95 FAT32
```

df -h:
```
Filesystem            Size Used Avail Use% Mounted on
/dev/hda2              30G  5.7G   23G  20% /
varrun               1014M  112K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  164K 1014M   1% /proc/bus/usb
udev                 1014M  164K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   23M  992M   3% /lib/modules/2.6.20-15-generic/volatile
/dev/hda4              35G  2.4G   33G   7% /media/fat32drive
/dev/hda1              26G   11G   15G  43% /media/windowsdrive
/dev/sdc2              32G  380M   32G   2% /media/disk

```

---

### Post by taurus on 2007-05-17
Can you post your /etc/fstab again?

```
cat /etc/fstab
```

---

### Post by PartisanEntity on 2007-05-17
sure

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=c2880040-c5b6-4606-82e2-1f13a887b953 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b1e22c16-5ed8-4e00-b4ec-249a422aa72e none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda4    /media/fat32drive vfat  iocharset=utf8,umask=000  0    0
/dev/hda1    /media/windowsdrive ntfs  nls=utf8,umask=0222 0    0
/dev/sdc1   /media/storage   ext2   defaults   0   0
```

---

### Post by taurus on 2007-05-17
And /dev/sdc1 doesn't mount to /media/storage when you run

```
sudo mount -a
df -h
```

---

### Post by PartisanEntity on 2007-05-17
> **taurus said:**
> And /dev/sdc1 doesn't mount to /media/storage when you run

```
sudo mount -a
df -h
```

It does. 

It just doesnt seem to run automatically when I attach the usb drive to the laptop.

---

### Post by PartisanEntity on 2007-05-22
If someone could help me solve this issue it would be really great, to reiterate what I want: I want my external usb hard-disk to mount the /dev/sdc1 partition under /media/storage every time I turn it on. The file system of this partition is ext3.

The hard-disk has another partition /dev/sdc2 which is FAT32, I don't care where it mounts.

---

### Post by Inxsible on 2007-05-22
> **PartisanEntity said:**
> If someone could help me solve this issue it would be really great, to reiterate what I want: I want my external usb hard-disk to mount the /dev/sdc1 partition under /media/storage every time I turn it on. The file system of this partition is ext3.
 
The hard-disk has another partition /dev/sdc2 which is FAT32, I don't care where it mounts.
 
You should use pmount and pumount to mount and unmount external drives. You do NOT need to create entries in fstab
 
First disconnect the drive, and then remove the entry for it from fstab. Having it in fstab will make Linux mount it every time and will give errors during boot if its not connected.
 
Now if you want to mount it as /media/storage, delete the folder. This is because pmount will not mount to an existing location.
```

sudo rmdir -f /media/storage

```
 
Now to mount your drive, connect it to your machine and enter
```

sudo pmount /dev/sdc1 /media/storage

```
 
This will create the /media/storage folder and mount the drive there.
 
Post back if you have problems or even if you get it fixed :)

---

### Post by PartisanEntity on 2007-05-22
I tried what you mentioned, it worked right after I entered the command, but every time I turn off the drive and turn it on again /dev/sdc1 and /dev/sdc2 will mount as /media/disk and /media/disk-1 (randomly, sometimes sdc1 is /disk and sometimes the other way round).

I would like /dev/sdc1 to mount at /media/storage without me having to do it manually every time, is that possible?

---

### Post by Inxsible on 2007-05-22
> **PartisanEntity said:**
> I tried what you mentioned, it worked right after I entered the command, but every time I turn off the drive and turn it on again /dev/sdc1 and /dev/sdc2 will mount as /media/disk and /media/disk-1 (randomly, sometimes sdc1 is /disk and sometimes the other way round).
 
I would like /dev/sdc1 to mount at /media/storage without me having to do it manually every time, is that possible?
We probably need to put an entry into etc/mtab, but I dont remember off the bat the syntax for it. Let me find out on my machine later in the evening and get back to you (Currently stuck at work :( )
 
EDIT : BTW, the /dev/sdc1 will not go away ... its just that you are creating a new mount point at /media/storage and so you can access the drive through both locations. Just thought I'd clarify that. When you switch off and switch the drive back on, does the /media/storage disappear ?

---

### Post by PartisanEntity on 2007-05-22
Thanks very much for the help so far :)

---

### Post by Inxsible on 2007-05-22
In the meanwhile, try this link:
 
Its a good how to on mounting hard drives - both internal and external
 
[http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)

---

