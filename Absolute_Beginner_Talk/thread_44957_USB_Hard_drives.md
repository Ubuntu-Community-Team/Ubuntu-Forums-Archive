---
title: "USB Hard drives"
date: 2005-06-28
forum: Absolute Beginner Talk
---

### Post by vampiro on 2005-06-28
Noobie here,

How do i get read, and modify access of the hard rive with out formatting it and starting again as it has some really important docs that i need. i have tried to change permsission but get a denied message and i dont know how to do it in console.


Cheers

---

### Post by Kyral on 2005-06-28
3 things:

What is it formatted in (NTFS, FAT32, etc)?

Paste the output from sudo fdisk -l (while it is turned on)

Paste your /etc/fstab file here.

'cause that question was quite vague  ;-)

---

### Post by vampiro on 2005-06-28
[QUOTE=Kyral]3 things:

What is it formatted in (NTFS, FAT32, etc)?

Paste the output from sudo fdisk -l (while it is turned on)

Paste your /etc/fstab file here.

'cause that question was quite vague  ;-)[/QUOTE]
 sorry about the vagueness of the Q

1. its formated in NTFS

2.
root@ubuntu:/home/vampiro # sudo fdisk -l

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1648    13237528+   7  HPFS/NTFS
/dev/hda2            1649        1741      747022+  82  Linux swap / Solaris
/dev/hda3            1742        2432     5550457+  83  Linux

Disk /dev/sda: 80.0 GB, 80026361856 bytes
32 heads, 63 sectors/track, 77530 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77529    78149200+   7  HPFS/NTFS

3.
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by gammyhand on 2005-06-28
[QUOTE=Kyral]3 things:

What is it formatted in (NTFS, FAT32, etc)?

Paste the output from sudo fdisk -l (while it is turned on)

Paste your /etc/fstab file here.

'cause that question was quite vague  ;-)[/QUOTE]
 I have a similar problem. My mp3 player is essentially picked up as an external hdd. It says it cannot read it as there is no filesystem (I know there is). What command do I use to examine the disk?

---

### Post by vampiro on 2005-06-28
](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by vampiro on 2005-06-28
](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by N'Jal on 2005-06-28
Um Ubuntu can't by default read NTFS since Microsoft has a patent on the NTFS.

---

### Post by vampiro on 2005-06-28
[QUOTE=N'Jal]Um Ubuntu can't by default read NTFS since Microsoft has a patent on the NTFS.[/QUOTE]
 ubuntu can read NTFS fine i can open files but they all be read only etc

---

### Post by poofyhairguy on 2005-06-28
[QUOTE=vampiro]Noobie here,

How do i get read, and modify access of the hard rive with out formatting it and starting again as it has some really important docs that i need. i have tried to change permsission but get a denied message and i dont know how to do it in console.


Cheers[/QUOTE]


Well...if you are having permissions problems you can always use a super nautilus with this command:

> gksudo nautilus

but be careful as you have a lot of power in that form.

---

### Post by Jussi Kukkonen on 2005-06-29
[QUOTE=vampiro]
How do i get read, and modify access of the hard rive with out formatting it and starting again as it has some really important docs that i need. i have tried to change permsission but get a denied message and i dont know how to do it in console.[/QUOTE]


Bad news, sorry. You can't write to a NTFS file system on linux (not safely anyway). Reading is fine, but for write access you'll need to change it to something else.

---

### Post by vampiro on 2005-06-29
[QUOTE=poofyhairguy]Well...if you are having permissions problems you can always use a super nautilus with this command:



but be careful as you have a lot of power in that form.[/QUOTE]
 thanks but that dosent help the files etc are still set to read only and i cant change permission

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=vampiro]thanks but that dosent help the files etc are still set to read only and i cant change permission[/QUOTE]


Sorry...I thought it was a permission problem. That would solve most. After reading the thread the problem is that Linux can only read NTFS. The drivers to write to NTFS can easily nuke your data so its not included with Ubuntu. They are unstable.

---

### Post by vampiro on 2005-06-29
so i have to convert it back to fat32 so that i can write to it, unless i create alll the docs again but when in ubuntu

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=vampiro]so i have to convert it back to fat32 so that i can write to it, unless i create alll the docs again but when in ubuntu[/QUOTE]

fat32 is the only fix format that both Linux and XP can read and write to.

---

### Post by gammyhand on 2005-06-30
[QUOTE=poofyhairguy]fat32 is the only fix format that both Linux and XP can read and write to.[/QUOTE]
 What about fat16? All I want to do is read from my mp3 player. I will reformat it for linux to write to after I have everything off it.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=gammyhand]What about fat16? All I want to do is read from my mp3 player. I will reformat it for linux to write to after I have everything off it.[/QUOTE]


FAT16 is so old...there is no reason to use it...it is WAY behind the times...but I'm sure Ubuntu could do things with it as well.

---

