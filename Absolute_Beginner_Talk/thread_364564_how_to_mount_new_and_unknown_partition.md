---
title: "how to mount new and unknown partition"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by nilsja on 2007-02-18
hi, i deleted my ntfs partition (hda2) with qtparted and created a new ext2 partition on this space. before reboot, i could write on this partition called disk. But after a reboot i can't find or mount a partition "disk". qparted shows the partition as hda2, but the folder /media/hda2 is empty and if i write in it, the mb are not recognized in qtparted used space...

so how to figure out how to mount this new partition?

---

### Post by taurus on 2007-02-18
Can you post these two here?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by nilsja on 2007-02-18
thanks for your fast response.> nils@nils:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1             196        1760    12570862+  83  Linux
/dev/hda2            1761        4863    24924847+  83  Linux
/dev/hda3               1         195     1566306   82  Linux swap / Solaris

Partition table entries are not in disk orderand> nils@nils:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=4b3f7ab5-af76-4490-b9e7-07d7504519a7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=2ED04B41D04B0F11 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=fd515b02-6eae-41e0-9936-1d6230fa5f6a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/usr/share/pycentral/gmailfs/site-packages/gmailfs.py /mnt/gmail gmailfs username=nilsjansen@gmail.com,password=xxx,fsname=zzzzz 
nils@nils:~$ before i deleted the ntfs partition, it was mounted in /media/hda2. now the folder /media/hda2 exists, but the data i wrote into "disk" are not in there...

---

### Post by solar george on 2007-02-18
Open a terminal type 
```
$ sudo mount /dev/hda2 /media/hda2
```

This will mount it however only root will be able to write to it.

To mount it more so that you can write to it you need to add a line to your /etc/fstab file.

Below is an example with the line that you need to add in bold.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                      /proc               proc      defaults                 0       0
/dev/hda1                /                   reiserfs  notail                    0       1
/dev/hdc           /media/cdrom0      iso9660  ro,user,noauto      0       0
/dev/fd0            /media/floppy0      auto       rw,user,noauto    0       0
**/dev/hda2        /media/hda2       ext           rw,user,noauto    0      0**

```

Open a terminal (in the accesories menu)

Type
```
sudo gedit /etc/fstab
```

Add the line in bold to the bottom of the file. Click save. Reboot

Now open a terminal (again) and type
```
mount /dev/hda2
```

It should mount allowing you to read and write.
It may automatically appear in the nautilus side bar and on your desktop but I'm not sure about that.

---

### Post by taurus on 2007-02-18
You need to edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line 

```

UUID=2ED04B41D04B0F11 /media/hda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

```
with this one.

```

/dev/hda2   /media/hda2   ext2   defaults   0   1

```
Save it and reboot.

---

### Post by nilsja on 2007-02-18
taurus an solar george: thank alot!

adding your hints together, i replaced in fstab> UUID=2ED04B41D04B0F11 /media/hda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1with> /dev/hda2       /media/hda2       ext2           rw,user,noauto    0      0
 and than mounted it, works fine.:) i'm now gonna reboot and check if its mounted automaticly...

---

