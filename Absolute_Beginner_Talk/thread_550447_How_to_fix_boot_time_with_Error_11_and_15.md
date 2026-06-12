---
title: "How to fix boot time with Error 11 and 15"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-09-13
I'm running from Feisty LiveCD.

I need to fix the booting system. 

It broke, because I followed another post about how to add a 2nd hard disk with the windows OS on it. The jumpers were set properly as: Pri. Master and Pri. Slave.

The post said I needed to add a "Windows" section to the /boot/grub/menu.lst

I added the section as indicated in that post.

When I rebooted, the Primary Master (Feisty ver. 7.04) could not be booted.

When boot time runs a while I received an Error 11 and when I try to select a kernel or recovery mode, I get Error 15 "file not found".

What needs doing to fix this?

---

### Post by huangweiqiu on 2007-09-13
Hi 

Because you have added a new partition,your linux partitions' IDs were already been changed.

Go in to you windows,and use you disk tool/manager to see your new partition column,find your linux main partition's new ID(number).

And then restart the computer,pls press the "e" while  you see grub,you will go into boot position editor,
just edit the numeral  to be your linux main partition 's new number-1.Eg ,your main partition's new number is 6,then you edit the boot position to be  (hd0,5).

-----------------------------------------

[www.linuxine.com](www.linuxine.com)  :lolflag:

---

### Post by Mark_in_Hollywood on 2007-09-13
I'm sorry, I can't follow your post very well. There were 2 disks, Pri. Mstr/Slave. I changed boot/grub/menu.lst. by adding a "windows" section. I turned computer off. changed pri-slave to a windows disk. Something went terribly wrong. I could not boot. I removed the windows disk, removed the section from menu.lst. Reinstalled the hard disk that had been in place when Feisty was installed. Now when I boot, I get nothing for an OS. There is a list, but nothing will boot. If I select a kernel .20 if I rmember, I get error 15, file not found. 

The windows disk and section of menu.lst is gone. Forever. I am trying to repair either Grub and maybe the MBR, I don't really know. Thanks, community.

---

### Post by huangweiqiu on 2007-09-13
Hi 

I had same problem before,I am sure my methods will work

Pls try.............

if you don't know your linux main partition ID,there is a way.pls boot with yr Ubuntu live cd ,and type :
sudo fdisk -l

on the terminal,you will see all your partitions' ID.

Pls try....

..............................

[www.linuxine.com](www.linuxine.com) :lolflag:

---

### Post by tgalati4 on 2007-09-13
Well, you learned that you can't swap disks willy-nilly.  Once a Linux system is set up, it expects the disks to remain in their places.  Of course, you can change them, but then you have to learn GRUB.  Sorry, those are the rules.  

There are lots of GRUB tutorials already on the forums.  Search "grub tutorial"

---

### Post by Mark_in_Hollywood on 2007-09-14
> **tgalati4 said:**
> Well, you learned that you can't swap disks willy-nilly.  Once a Linux system is set up, it expects the disks to remain in their places.  Of course, you can change them, but then you have to learn GRUB.  Sorry, those are the rules.  

There are lots of GRUB tutorials already on the forums.  Search "grub tutorial"

This response is not a help. PERIOD.

I didn't "swap disks willy-nilly" you yoctocerebral, ninnyhammering, gormless TWIT!

Get out of this thread, unless you have something material to contribute. I spent HOURS reading how to (supposedly) add an extra disk. Willy-nilly. What the hell do you know about it?

---

### Post by Mark_in_Hollywood on 2007-09-14
[QUOTE=huangweiqiu;3362031]Hi 
I had same problem before,I am sure my methods will work
Pls try.............
if you don't know your linux main partition ID,there is a way.pls boot with yr Ubuntu live cd ,and type :
sudo fdisk -l
on the terminal,you will see all your partitions' ID.
Pls try....
..............................


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4485    36025731   83  Linux
/dev/sda2            4773        4865      747022+   5  Extended
/dev/sda5            4773        4865      746991   82  Linux swap / Solaris

Disk /dev/sdb: 10.2 GB, 10202050560 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1181     9486351   83  Linux
/dev/sdb2            1182        1240      473917+   5  Extended
/dev/sdb5            1182        1240      473886   82  Linux swap / Solaris

---

### Post by huangweiqiu on 2007-09-14
Device Boot Start End Blocks Id System
/dev/sda1 * 1 4485 36025731 83 Linux
/dev/sda2 4773 4865 747022+ 5 Extended
/dev/sda5 4773 4865 746991 82 Linux swap / Solaris

....

Hi 

for example,if your ubuntu was intall in sda2 ,then your boot position should be (hd0,1). *partition numeral -1

press "e" while you see the grub menu you will go into boot editor,and then follow the instruction ,it is easy ,don't worry.

I don't know your ubuntun was intalled in which partition,but absolutely is not sda5,as it is a swap partition.

good luck!


-----------------------

[www.linuxine.com:lolflag:](www.linuxine.com:lolflag:)

---

