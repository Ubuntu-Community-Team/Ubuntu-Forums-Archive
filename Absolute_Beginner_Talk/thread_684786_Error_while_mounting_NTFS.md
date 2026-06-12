---
title: "Error while mounting NTFS"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by shashank86 on 2008-02-01
Hi
I installed kubuntu 6.06 a few hours ago and have absolutely no clue as to configuring it... My first concern is that even though my drives are recognized there is an error occurring when i try mounting it..

The pop up says:

Could not mount device.
The reported error was:
mount: can't find /dev/sda6 in /etc/fstab or /etc/mtab

Thanks in advance...

PS: If i have to give any more info please do mention how to get it as well. Thanks

---

### Post by jan quark on 2008-02-01
run in terminal and post result please

```
mount
```

```
sudo fdisk -l
```

```
ls /dev/disk/by-uuid -alh
```

---

### Post by iansane on 2008-02-01
Looks like you need to make an fstab entry but Jan Quark is probably about to get to that so I'll stay out of it and go eat lunch. :-)

---

### Post by erfahren on 2008-02-01
to read/write to it you'll need ntfs-3g - it's not available in the Dapper repositories - see: 
[HOWTO: NTFS with read/write support using ntfs-3g (easy method)](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by shashank86 on 2008-02-01
> **jan quark said:**
> run in terminal and post result please

```
mount
```

```
sudo fdisk -l
```

```
ls /dev/disk/by-uuid -alh
```

for

mount

```


/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)



```

sudo fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         638     5124703+   7  HPFS/NTFS
/dev/sda2             639        8963    66870562+   f  W95 Ext'd (LBA)
/dev/sda3            8964        9729     6152895   83  Linux
/dev/sda5             639        3826    25607578+   7  HPFS/NTFS
/dev/sda6            3827        8288    35840983+   7  HPFS/NTFS
/dev/sda7            8289        8925     5116671    7  HPFS/NTFS
/dev/sda8            8926        8963      305203+  82  Linux swap / Solaris
```

ls /dev/disk/by-uuid -alh
```
total 0
drwxr-xr-x 2 root root 140 2008-02-03 00:09 .
drwxr-xr-x 5 root root 100 2008-02-03 00:09 ..
lrwxrwxrwx 1 root root  10 2008-02-03 00:09 12A4D9CBA4D9B189 -> ../../sda6
lrwxrwxrwx 1 root root  10 2008-02-03 00:09 30B0E814B0E7DE7A -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-02-03 00:09 7CEC2B03EC2AB774 -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-02-03 00:09 C640B9B340B9AB17 -> ../../sda7
lrwxrwxrwx 1 root root  10 2008-02-03 00:09 f0d0f1d5-e85c-44ef-88d2-f5b5fcbccf21 -> ../../sda3

```

---

### Post by erfahren on 2008-02-01
also post the output of:
```

cat /etc/fstab

```
and if you could 
```

blkid

```
(I think the results from the second one are easier to read)

---

### Post by shashank86 on 2008-02-01
i got this for the first one
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda8       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

For the second line there was nothing

---

### Post by jan quark on 2008-02-01
use this command to have a look in the media folder

```
ls /media
```

are there already some mount points like hda1 or similar 
if yes try to navigate to the via the nautilus file manager or just open the places > computer> filesystem > media

can you see your partitions there ?


if no 
we create them manually 

 I see four diefferent ntfs partions
              
Boot
/dev/sda1   *           1         638     5124703+   7  HPFS/NTFS
/dev/sda5             639        3826    25607578+   7  HPFS/NTFS
/dev/sda6            3827        8288    35840983+   7  HPFS/NTFS
/dev/sda7            8289        8925     5116671    7  HPFS/NTFS

we will make four mount points for them 
datapartition in only a name choose yours

```
sudo mkdir /media/datapartition1
```
```
sudo mkdir /media/datapartition2
```
```
sudo mkdir /media/datapartition3
```
```
sudo mkdir /media/datapartition4
```



now we mount them

```
sudo mount /dev/sda1 /media/datapartition1 -t ntfs -o nls=utf8,umask=0744
```
```
sudo mount /dev/sda5 /media/datapartition2 -t ntfs -o nls=utf8,umask=0744
```
```
sudo mount /dev/sda6 /media/datapartition3 -t ntfs -o nls=utf8,umask=0744

``````
sudo mount /dev/sda7 /media/datapartition4 -t ntfs -o nls=utf8,umask=0744
```

---

### Post by shashank86 on 2008-02-01
> **jan quark said:**
> use this command to have a look in the media folder

```
ls /media
```

are there already some mount points like hda1 or similar 
if yes try to navigate to the via the nautilus file manager or just open the places > computer> filesystem > media

can you see your partitions there ?


if no 
we create them manually 

 I see four diefferent ntfs partions
              
Boot
/dev/sda1   *           1         638     5124703+   7  HPFS/NTFS
/dev/sda5             639        3826    25607578+   7  HPFS/NTFS
/dev/sda6            3827        8288    35840983+   7  HPFS/NTFS
/dev/sda7            8289        8925     5116671    7  HPFS/NTFS

we will make four mount points for them 
datapartition in only a name choose yours

```
sudo mkdir /media/datapartition1
```
```
sudo mkdir /media/datapartition2
```
```
sudo mkdir /media/datapartition3
```
```
sudo mkdir /media/datapartition4
```



now we mount them

```
sudo mount /dev/sda1 /media/datapartition1 -t ntfs -o nls=utf8,umask=0744
```
```
sudo mount /dev/sda5 /media/datapartition2 -t ntfs -o nls=utf8,umask=0744
```
```
sudo mount /dev/sda6 /media/datapartition3 -t ntfs -o nls=utf8,umask=0744

``````
sudo mount /dev/sda7 /media/datapartition4 -t ntfs -o nls=utf8,umask=0744
```

i think the drives are mounted,,, there is a green flag at its right bottom,,, but now it says i do not have enough permission to read... what should i do???

---

### Post by jan quark on 2008-02-01
navigate in the terminal to the drives you mentioned
for instance

me@desktop: cd /media/data1

and run the following command

```
ls -l
```

this will show the permissions set

post the result

---

### Post by jan quark on 2008-02-01
when you come back

to set the permission to the new drives
do the following
```

sudo chmod -R 744 /media/data1 or whatever name you have chosen
```

---

### Post by shashank86 on 2008-02-02
Sorry man.. had to get some serious sleep.. 
Anyway when i run 
Code 1
```
ls -l
```
i get a permission denied line
if i run this
Code 2
```
sudo ls -l 
```
i get a list of the directories on the drive
running this code changes the permission of every file on the drive
```
sudo chmod -R 744 /media/datapartition1 
```
but i still get a permission denied line error if i run the first code and the second code works.

---

