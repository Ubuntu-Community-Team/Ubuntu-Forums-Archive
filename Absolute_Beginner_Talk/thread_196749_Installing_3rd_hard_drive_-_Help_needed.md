---
title: "Installing 3rd hard drive - Help needed"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by lonegranger on 2006-06-14
My PC has 3 hard drives. When I was running XP it recognised all 3 therefore the BIOS must be set ok. The one I have on IDE 3 just is not recognised by Dapper. The motherboard is a Gigabyte K7 Triton GA-7N400-Pro2

Any ideas gratefully received

---

### Post by LadyLuck on 2006-06-14
what responce to you get if you run 
sudo fdisk -l
in a command window?

---

### Post by bruce89 on 2006-06-14
Is there any mention of it in System>Administration>Disks?

---

### Post by lonegranger on 2006-06-14
If the command line you suggest end with minus pipe -| then all I get is a greater than sign > on the next line down.

---

### Post by LadyLuck on 2006-06-14
no sorry it is a small L the letter l (looks like a pipie I know)

---

### Post by bruce89 on 2006-06-14
[QUOTE=lonegranger]If the command line you suggest end with minus pipe -| then all I get is a greater than sign > on the next line down.[/QUOTE]
No, I think is was supposed to be a l (L)

---

### Post by lonegranger on 2006-06-14
No - it shows my 2 hard drives, my 2 CD drives although they are both DVD drives and my floppy drive

---

### Post by lonegranger on 2006-06-14
The fdisk command in the terminal shows :-

Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          96       48163+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/hda2          150901      155060     2096609    f  W95 Ext'd (LBA)
/dev/hda3              96      150897    76003515   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda5          150901      155060     2096608+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+   7  HPFS/NTFS

---

### Post by LadyLuck on 2006-06-14
In your /etc directory there is a file called fstab (filesystem table or something the like). There should be lines in it describing how the different partitions are  (should be) mounted. What does it look like? 
You third disk is a single ntfs partition I assume.

---

### Post by lonegranger on 2006-06-14
sorry bit new to this - I've found fstab but how do I open it to see what it contains and yes the 3rd drive should be a single NTFS partition

---

### Post by LadyLuck on 2006-06-14
Ther are a whole host of text editors you can use. For historical reaons I still use "pico" so I write

pico /etc/fstab

and the file opens. If you in the future have to change this file you must open it as superuser with

sudo pico /etc/fstab

you wiill then be promted for your password. Oh and if you are  already in the etc directory you can skip the /etc/ part and just use the file name.

---

### Post by lonegranger on 2006-06-15
I was online to the forum last night with my hard drive problem and had to leave before I could finish the help I was getting. If the same people who were helping I would appreciate continuing. Below is the what was asked before I had to log off which was what does the fstab file contain.

Appreciate further help.  

/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext2    defaults        0       2
/dev/hdb1       /media/hdb1     ntfs    user,umask=0200        0       0
/dev/hdb5       /media/hdb5     ntfs    user,umask=0200        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

