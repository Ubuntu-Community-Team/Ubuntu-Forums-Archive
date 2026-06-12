---
title: "need some advice"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by Roofie on 2006-12-24
Am very new to linux mayby 3-4weeks now
so my troubles im having i have had ubuntu installed close to 4 weeks now on 160 gig maxtor hd
i also have windows xp installed on 40gig maxtor hd patitioned at 15 gig
So wanted to try another version of linux,so i installed the last stable version of debian on the remaining 25 gig.
Well now i can boot windows and im on the newly installed debian.But when i try to boot ubuntu this is what i get:

BusyBox v.1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter Help for a list of built-in commands.

/bin/sh:cant access tty; job control turned off
(initramfs)

So my system is 
Asus A8V-UAYZ
Amd 3500+
1gig DDRram stick 
512 DDR Ram stick
Ati video card
hd maxtor 160 gig
hd maxtor 40 gig

I now after time i will learn all this 6 years with windows and im only a couple weeks with linux.
Is there anyway to get ubuntu to come back easily or better to reinstall and hope i can still get back into windows and debian?
Thank you for any help

---

### Post by viniosity on 2006-12-24
Can you post your partition scheme?  from debian you might try:

su - 
(then enter your root password)

cfdisk

(jot down what you see and post that here)

it might help to know what choices you made when installing debian with regards to where you put the root partition, home partition, swap, etc

---

### Post by Roofie on 2006-12-24
So here is what i came up with:
                                  cfdisk 2.12p

                              Disk Drive: /dev/hda
                        Size: 40982151168 bytes, 40.9 GB
              Heads: 255   Sectors per Track: 63   Cylinders: 4982

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hda1        Boot        Primary   NTFS             []              13629.29
    hda2                    Primary   Linux ext3       [/]             26205.75
    hda5                    Logical   Linux swap / Solaris              1143.32









     [Bootable]  [ Delete ]  [  Help  ]  [Maximize]  [ Print  ]
     [  Quit  ]  [  Type  ]  [ Units  ]  [ Write  ]

                 Toggle bootable flag of the current partition

So to me im not seeing the biggest hd maxtor 160gig 
Does this make sence?

---

### Post by Sef on 2006-12-24
> Can you post your partition scheme? from debian you might try:

su -
(then enter your root password)

cfdisk



Actually a much safer way to check your partitions is this:

> sudo fdisk -l

Then just copy and paste here.

---

### Post by Roofie on 2006-12-24
Ok so after reinstalling ubuntu all is now good
I can boot all 3 operating systems!
Thanks for the help 
O yah here is what i came up with in ubuntu:

roofie@roofie-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1657    13309821    7  HPFS/NTFS
/dev/hda2            1658        4843    25591545   83  Linux
/dev/hda3            4844        4982     1116517+   5  Extended
/dev/hda5            4844        4982     1116486   82  Linux swap / Solaris

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19363   155533266   83  Linux
/dev/hdb2           19364       19929     4546395    5  Extended
/dev/hdb5           19364       19929     4546363+  82  Linux swap / Solaris
roofie@roofie-desktop:~$ 


Again Thanxs and Happy Holidays to all

---

### Post by Sef on 2006-12-24
You're welcome.   Please post any other questions that you have.

---

