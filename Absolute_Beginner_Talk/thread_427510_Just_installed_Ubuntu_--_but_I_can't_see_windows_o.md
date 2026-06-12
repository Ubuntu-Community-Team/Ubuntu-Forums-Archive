---
title: "Just installed Ubuntu -- but I can't see windows on GRUB"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by MrMatt2532 on 2007-04-29
I have 3 partitions (1 hd), 2 for ubuntu and 1 for windows xp, and they are grouped as shown:
/dev/sda1
     /dev/sda5 -- windows
     /dev/sda6 -- swap partition
/dev/sda2 -- ubuntu

I don't know why they are grouped like this, but after i installed ubuntu, windows xp didn't show up on the grub boot loader.

I tried:

title Windows
root (hd0,0)                            <--also with (hd0,5)
makeactive
chainloader +1 

and 

title Windows
rootnoverify	(hd0,0)             <--also with (hd0,5)
savedefault
makeactive
chainloader	+1

both with no success. Can someone help me out here? Thanks.

---

### Post by louieb on 2007-04-29
Kinda weird that XP is on a logical partition. But your on the right track trying to adjust  the root statment.
Lets make sure. list your partition table: open applications>accessories>terminal
```
sudo fdisk -l
```
(lowercase L)

Post it here if you need some more help.

---

### Post by annda on 2007-04-29
by the way, it should be (hda0,4) linux starts counting from 0.

---

### Post by MrMatt2532 on 2007-04-29
here are my fdisk results:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        4061    32611950    f  W95 Ext'd (LBA)
/dev/sda2   *        4062        7296    25985137+  83  Linux
/dev/sda5               2        3916    31447206    7  HPFS/NTFS
/dev/sda6            3917        4061     1164681   82  Linux swap / Solaris

I'll try with (hda0,4)

---

### Post by MrMatt2532 on 2007-04-29
> **MrMatt2532 said:**
> I'll try with (hda0,4)

This didn't work...

---

### Post by annda on 2007-04-29
you don't really need rootnoverify if the partitions are all on the same disk. here's my entry for sda2:


> title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

it could be that GRUB needs some extra configuration for windows on a logical drive. i know linux doesn't, but i have no idea about windows, sorry.

---

### Post by MrMatt2532 on 2007-04-29
bump -- any other advice?

---

### Post by Terl on 2007-04-29
> **MrMatt2532 said:**
> This didn't work...

It would be (hd0,4) - no a

Mine looks like:

```
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

Yours should be similar but with (hd0,4) where I have (hd0,0)

---

### Post by MrMatt2532 on 2007-04-29
This is what i currently have, and it doesn't work:

title Microsoft Windows XP Professional
root (hd0,4)
savedefault
makeactive
chainloader +1

---

### Post by bobplano on 2007-04-29
i think hd0,5 or whatever is for ide drives. it seems you have sata, so try sda0,5

---

### Post by louieb on 2007-04-29
> **MrMatt2532 said:**
> This is what i currently have, and it doesn't work:

I wonder how XP got installed in a logical partition in the first place. I've heard that XP doesn't work if installed in a logical partition.   [Found this workaround]("http://tech.groups.yahoo.com/group/xosl/message/2864"). But it seems to easier just to start over from scratch.

---

### Post by webbaw on 2007-08-04
I have the same problem and I dont understand how hd0 etc relates to the drives on my machine.

I've fiddled with the commands as per the previous post but cant get Windows to boot.  I have 2 drives on my system.  Windows is on the default ide drive and Ubuntu is on the second ATA drive.

Here is the sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdb2            6375       38912   261361485    f  W95 Ext'd (LBA)
/dev/sdb5            6375       12748    51199123+   7  HPFS/NTFS
/dev/sdb6           12749       38912   210162298+   7  HPFS/NTFS

What bootloader commands do I need so I get a Windows XP option that works?

Thanks.

Andrew

---

### Post by charlier653 on 2007-08-04
It doesn't.

Use sd(0,?) or sd(1,?) [insert proper partition for ?]  instead of hd(?,?)

---

### Post by webbaw on 2007-08-04
Thanks for your help and your quick reply.  Just tried that but no luck.  The error I get with sd is "Error while parsing number".  This is the same for sd0,1 and sd1,0 and sd0,0

Here is my grub boot loader menu.lst...

title		Windows XP
root		(sd1,0)
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=80a50ef2-6924-41ed-97fc-21984fc26a62 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=80a50ef2-6924-41ed-97fc-21984fc26a62 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=80a50ef2-6924-41ed-97fc-21984fc26a62 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=80a50ef2-6924-41ed-97fc-21984fc26a62 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


Ubuntu works fine with hd.

---

### Post by coolen on 2007-08-04
> **charlier653 said:**
> It doesn't.

Use sd(0,?) or sd(1,?) [insert proper partition for ?]  instead of hd(?,?)

Grub doesn't care about sda/hda. They both use hdX.

---

