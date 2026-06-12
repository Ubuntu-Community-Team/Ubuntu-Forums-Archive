---
title: "Quite weird"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by josealarcon on 2006-03-31
I know it can sound strange , but i received my instalation CDs today (thanks to the Canonical) , and when i´ve tried to install , the installer does not read the partitions i´ve done in the #1 HD . Are there any reasons for this ?.
Before this I´ve tried to install Ubuntu dowloading it from the web and whith that installer version I saw the partitions and created new ones that were recognized by WXP and W98 ,that are already installed in my computer.

Thanks a lot

Jose

---

### Post by Pragmatist on 2006-03-31
Try using the LiveCD and type this:

```
sudo fdisk /dev/hda
```

Then at the menu, type 'p' for print partition table.  Then give us that information.

---

### Post by josealarcon on 2006-03-31
I did it , this is what I get 

Disk /dev/hda: 20.0GB 20020396032 bytes
255 heads   63 sectors/track   2434 cylinders
Units: cylinders of 16065.512=8225280 bytes

Device		boot	Start	End	Blocks		Id	System
/dev/hda1	*	1	487	3911796	       b       W95 FAT32
/dev/hda2		488	2434	15639277+    f	     W95(ext LBA)
/dev/hda3		2018	2434	3349521	      7	      HFPS/NTFS
/dev/hda5		488	749	2104452  	b      W95 FAT32	
/dev/hda6		750	811	497983+	       83     Linux swap/solaris
/dev/hda7		812 	2017	9687163+       b     W95 FAT32

Please tell me what´s wrong....!

Thanks again

---

### Post by Sef on 2006-04-01
Did you try more than one disk?  Sometimes the disks are bad.

---

### Post by josealarcon on 2006-04-01
Disks are OK , they are working with WXP and W98

---

### Post by taurus on 2006-04-01
[QUOTE=josealarcon]Disks are OK , they are working with WXP and W98[/QUOTE]
I think he meant the CD!!!

---

### Post by Pragmatist on 2006-04-01
>  Originally Posted by: **josealarcon**
Device        boot    Start    End    Blocks        Id    System
/dev/hda1    *    1    487    3911796     b W95 FAT32
/dev/hda2        488    2434    15639277+ f     W95(ext LBA)
/dev/hda3        2018    2434    3349521     7     HFPS/NTFS
/dev/hda5        488    749    2104452     b W95 FAT32    
/dev/hda6        750    811    497983+     83 Linux swap/solaris
/dev/hda7        812     2017    9687163+ b W95 FAT32
   
 I see several problems here:
 
 1.)** partition sizes add up to more than total disk size.**  /dev/hda1 /dev/hda2 and /dev/hda3 add up to more than 20GB and drive is 20GB 
 
This is the size of your drive..................[B]20020396032 bytes
[/B]This is the size of hda1 + hda2 + hda3                        [B]22900594000 bytes

[/B]I believe this is made up for by hda5 hda6 and hda7 adding up to less than their extended partition (hda2)

2.) You have a swap partition (/dev/hda6 whose code should be 82 not 83) but **you don't have a regular linux partition!**  You need a partition of type ext3 to mount root (/)
 
Is there anything on this disk that you need? If not, I would start over by using fdisk to delete the partitions and then create new ones.
 
 If you do need what is on the disk, then use a partition utility (like **parted**) with the LiveCD to repartition the disk
 
 When you repartition, all you need for Linux is:
 
1.) A main Linux partition to mount / use ext3 (type 83) probably want at least 5GB here. could use much less, it just depends on how full a system you want.
 2.) A swap partition  use swap type (type 82) make 1-3 times the size of RAM
 
 That's it!

---

