---
title: "Will not boot without CD"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by crewfan on 2007-08-29
I've tried searching for answers to this, but have not had any luck.

When I try to boot Ubuntu with out the CD, I get "bootable device not found."  I only have one hardrive with only Ubuntu installed.

Thanks for your help!

---

### Post by Duck2006 on 2007-08-29
Did you load grub? If not this may help

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by WebSiteGuru on 2007-08-29
What type of drive is it? SATA? IDE?...

---

### Post by kellemes on 2007-08-29
You're sure your harddisk is listed as bootable in BIOS?

---

### Post by mysticmatrix on 2007-08-29
This might help you. I also faced the same trouble when I installed Feisty on a brand new assembled PC with full install. The trouble seems to be that Ubuntu doesn't makes the default partition boot partition.

This can be checked if you do the following.

1) Boot with the live CD
2) Select the option 'Boot from (1st) Hard disk'

This should hopefully start your ubuntu from hard disk.

Now open system monitor from System --> Administration menu and look at last tab. This should list your device on which root directory, i.e. / is mounted. I have attached screenshot of mine which shows /dev/sda11

 Once there, open terminal from Application --> Accesseries --> Terminal


3) Now type or copy-paste following
```

sudo fdisk /dev/sda
```

Note that I have written 'sda' as my disk was /dev/sda11. Your might be /dev/hdc2 or something like that. Just drop the numbers and write proper /dev/[whatever]

3) Typr in your user password. Then press 'l' (the letter 'l' as in 'L'ion) and press enter. This will show you a table of your partitions something like this

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       30400   223215142+   f  W95 Ext'd (LBA)
/dev/sda5            2612        6527    31455238+   7  HPFS/NTFS
/dev/sda6           10571       10819     2000061   82  Linux swap / Solaris
/dev/sda7           10820       17346    52428096    7  HPFS/NTFS
/dev/sda8           17347       23873    52428096    7  HPFS/NTFS
/dev/sda9           23874       30400    52428096    7  HPFS/NTFS
/dev/sda10           8704       10570    14996646   83  Linux
/dev/sda11           6528        8703    17478688+  83  Linux

```

Again yours might be different. Note that one of my partitions has a boot flag shown by *. If your table has no boot flag, we have got the problem.

Now press 'a' and press enter. Then type in the correct number of your partition.

Once done, press 'w' and exit the terminal by closing it. Reboot and you are done!(Hopefully)

Cheers

---

### Post by crewfan on 2007-08-30
Mysticmatrix,

Your suspicions were correct.  There was no * by my sda1.  Thanks again for the detailed instructions!

---

