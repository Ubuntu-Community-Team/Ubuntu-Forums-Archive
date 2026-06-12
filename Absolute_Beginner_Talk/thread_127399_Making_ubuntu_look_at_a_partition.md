---
title: "Making ubuntu look at a partition"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by shickidyshade on 2006-02-08
ok i have a dell latitude d610 and i am trying to make ubuntu find my partition but i can't can anybody hel

---

### Post by TrendyDark on 2006-02-08
what type of partition is it? FAT32, NTFS (windows partition?)

---

### Post by paulmilliken on 2006-02-08
[QUOTE=shickidyshade]ok i have a dell latitude d610 and i am trying to make ubuntu find my partition but i can't can anybody hel[/QUOTE]
Please post the output of "sudo less /etc/fstab".  Also, can you describe the partition that you are looking for?  For example, is it a windows partition and do you know what file format it uses?

---

### Post by shickidyshade on 2006-02-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
(END)

it is a partition between windows and linux 
I think its a fat 32 but im not 100% sure

---

### Post by shickidyshade on 2006-02-08
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3848    30909028+   7  HPFS/NTFS
/dev/sda2            3849        5888    16386300    c  W95 FAT32 (LBA)
/dev/sda3            5889        7234    10811745   83  Linux
/dev/sda4            7235        7296      498015    5  Extended
/dev/sda5            7235        7296      497983+  82  Linux swap / Solaris

---

### Post by TrendyDark on 2006-02-08
```

sudo mkdir /media/drive2
sudo mount /dev/sda2 /media/drive2/ -t vfat -o iocharset=utf8,umask=000

```

I'm going to assume it's the sda2 fat32 partition. If that is so, the above should work. Just enter it in your terminal.

If that is not the correct partition, just look in the commands i gave you and swap the "/dev/sda2" part with the correct one.

---

### Post by shickidyshade on 2006-02-09
this worked but i restarted my computer but it disapperead why did this happen

---

### Post by shickidyshade on 2006-02-09
can i change the name of it

---

### Post by aysiu on 2006-02-09
[QUOTE=shickidyshade]this worked but i restarted my computer but it disapperead why did this happen[/QUOTE] See the fourth link of my signature.

---

### Post by shickidyshade on 2006-02-09
ok so i got to the sudo nano /etc/fstab and this is what i got im confused

  GNU nano 1.3.8             File: /etc/fstab                         Modified

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


can anybody understand this
I'm trying to learn

---

### Post by shickidyshade on 2006-02-09
ok so i got to the sudo nano /etc/fstab and this is what i got im confused

  GNU nano 1.3.8             File: /etc/fstab                         Modified

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


can anybody understand this
I'm trying to learn

---

