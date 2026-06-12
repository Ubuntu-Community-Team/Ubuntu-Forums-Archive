---
title: "Mount drive automatically."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by cumanzor on 2007-05-09
I currently have 2 drives. On the first drive I have my XP partition, and my Ubuntu partition. On the second drive I have a NTFS partition (where I keep all my photos, music and videos) and a FAT32 partition that I use as a bridge (to move files <-> windows).

All partitions are automatically mounted when I start my system except for the FAT32 one, which would be sdb2 I guess. I think this happens because I made this partition after installing ubuntu. I was told to add the partition to the fstab file, but I don't have any clue what to do. Here is the file.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=e5508af4-36ec-412b-8b09-bf863ef6f767 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=DAB8E591B8E56D07 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=EC9E721C4FB4002D /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=11b2a0a9-88fa-44cd-b456-64ee8663ef7a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


This is the original file made by the ubuntu installer. First of all, how do I add sdb2 (note that I'm not even sure if this is the drive) to the fstab?

---

### Post by earobinson on 2007-05-09
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by oilchangeguy on 2007-05-09
read this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Nythain on 2007-05-09
first you have to create a place to mount it, something like
sudo mkdir /bridge
then as far as the entry into fstab, it should look something like this
/dev/sdb2     /bridge    vfat     defaults    0   0
that should do the trick

---

### Post by Skrynesaver on 2007-05-09
Copy the output from
```

sudo vol_id /dev/sdb2

```
then 
```

sudo mkdir /media/VFAT
gksudo gedit /etc/fstab

```
Now add the following lines to your fstab
```

#/dev/sdb2
UUID=<Output_of_vol_id> /media/VFAT vfat    defaults 0       1

```
now simply
```

sudo mount -a

```

---

### Post by Scunizi on 2007-05-09
As an added thought, if your Fat32 partition is still empty, consider formatting it with ext3 then in windows load the driver for ext3 access.  If you've already used ext3 as your primary filesystem for your ubuntu install, just load the driver in Windows and away you go!  You can also recover that fat32 disk space back into your primary partition for ubuntu.  Check out [http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html](http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html)

---

### Post by cumanzor on 2007-05-09
That did it thanks everyone.

@Scunizi: I'll try that sometime later. I was also thinking of ntfs-3g, but I don't know how reliable it is.

---

### Post by Inxsible on 2007-05-09
I have all my drives including External Drives formatted to EXT3. It works great !!
 
I use FS-Driver from Windows Vista to access the EXT3 partitions. and NTFS-3G to access the 1 windows partition I have in my dual boot.
 
 
Slowly and steadily...I think I might just throw Vista out. Whatever I have seen in Vista -- not so great ;)

---

