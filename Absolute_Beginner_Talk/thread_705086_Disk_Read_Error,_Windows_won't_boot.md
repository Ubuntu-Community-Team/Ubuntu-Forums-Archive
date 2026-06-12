---
title: "Disk Read Error, Windows won't boot"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Papa.Gario on 2008-02-23
After installing Ubuntu, I can't get into Windows because I get and error stating "disk read error"

I've tried repairing, I've tried reinstalling grub, and I've tried reinstalling Ubuntu.  

I'm lost.  I've read as many other forum posts as I can, but I can't really find answers -- is there a FAQ that can walk me thru this?  Or can someone help a lowly linux newbie?:(

---

### Post by zxscooby on 2008-02-23
post the output of 
```
sudo fdisk -l 
```

and your 
/boot/grub/menu.lst

---

### Post by polmir on 2008-02-23
Have You two system (Ubuntu and Windows) or only one (Ubuntu)?

---

### Post by Papa.Gario on 2008-02-23
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14991   120415176    7  HPFS/NTFS
/dev/sda2           37764       38913     9230760    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           14992       15667     5429970   82  Linux swap / Solaris
/dev/sda4           15668       27825    97659135   83  Linux

Partition table entries are not in disk order

```

And Grub shows something like root 0,0 for windows -- changing it to 0,1 boots the HP recovery.

I'm sorry polmir, but I'm not sure if I understand your question.  I have one hard drive that had Window XP media edition on it, and I installed Ubuntu.  After the installing I can only access Ubuntu.

This is from PC Doctor:

Drive Partition HP_RECOVERY
Drive: C
Usable Capacity: 8.79
Used Space: 8.34
File System: FAT32

Drive Partition: HP_PAVILION
Drive: D
Usable Capacity: 114.84
Used Space: 45.57
File System: NTFS


I thought C was my main drive, and D was the recovery? Why would it show it as different now? Did it change when I did the partition during the Ubuntu Install?

Sorry about the two different threads -- forgot I posted these.

---

### Post by Papa.Gario on 2008-02-23
I'm still having problems with this, any advice?

---

### Post by Papa.Gario on 2008-02-24
I've tried repairing windows too from the HP recovery, nothing seems to work.

I've tried the super grub cd, no luck with that.

Any other suggestions?

I can see all my files on the disk in the windows partition, it just wont boot -- I've been trying to find solutions on the microsoft website, but no luck there either.

---

### Post by polmir on 2008-02-24
Please red this >>[Preparation_For_The_Install]("http://www.users.bigpond.net.au/hermanzone/p17.htm#Preparation_For_The_Install_")<<

---

### Post by Papa.Gario on 2008-02-24
Thanks Polmir.  I read most of the info on the link, tried gag, and read most of the info on the gag links but no luck.

Most of the stuff listed there is preventative stuff.  I don't have a windows recovery disk at the moment so I'm at a loss as for what I should do.

I need to find a way to fix my MBR but .. yeah.

---

### Post by polmir on 2008-02-24
for Windows
```
fdisk /mbr
``` 
```
 fixmbr
```

copy mbr --- Linux
```
dd if=/dev/hda of=/home/folder/mbr.img bs=512 count=1
```
recover mbr --- Linux
```
dd if=/home/folder/mbr.img of=/dev/hda bs=512 count=1
```

Try it:
>>[SystemRescueCd]("http://www.sysresccd.org/Main_Page")<<

---

### Post by Papa.Gario on 2008-02-24
Thanks, I'm downloading it now, I hope it works!

I tried fdisk /mbr and that didn't do anything other than get rid of grub, I'm hoping fixmbr will work.  

I'll post the results when I try it.

---

