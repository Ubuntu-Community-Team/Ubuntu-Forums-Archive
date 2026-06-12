---
title: "Should I Be Worried If..."
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by money2themax on 2008-01-06
Should I be worried if this is missing ```
/dev/sda
```

---

### Post by lolzlolz on 2008-01-06
depends what was there in the first place, if you were me you'd be worried because my main hardrive is attached there
the second hard drive is at /dev/sdb
so it depends where your hardrives are and how they are arranged,
more info on how you found out this was missing/ are there any problems because it's missing if there arent there's no need to worrk :)

---

### Post by money2themax on 2008-01-06
i have a SATA and a IDE <-- my main

---

### Post by Rocket2DMn on 2008-01-06
If all your drives are accounted for, then there is nothing to worry about.  You can check by running
```
sudo fdisk -l
```

---

### Post by lisati on 2008-01-06
> **lolzlolz said:**
> depends what was there in the first place, if you were me you'd be worried because my main hardrive is attached there
the second hard drive is at /dev/sdb
so it depends where your hardrives are and how they are arranged,
more info on how you found out this was missing/ are there any problems because it's missing if there arent there's no need to worrk :)

+1

---

### Post by money2themax on 2008-01-06
> **Rocket2DMn said:**
> If all your drives are accounted for, then there is nothing to worry about.  You can check by running
```
sudo fdisk -l
```
call me what you will but what will that do?

---

### Post by Rocket2DMn on 2008-01-06
That will show you the connected drives and partitions (if the disk is mounted).  So if you have 2 internal drives, you probably have sda and hda, though it could vary.

---

### Post by PeterJS on 2008-01-06
fdisk is the command line partition editor and manager and the -l option tells it to list all the current partitions and then exit. In this case the sudo isn't needed unless you used bastile to lock your system down.

---

### Post by lolzlolz on 2008-01-06
+1 wat do you mean???

---

### Post by money2themax on 2008-01-06
this is what came up
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02e0c953

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/hdc: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3577    28732221   83  Linux
/dev/hdc2            3578        3736     1277167+   5  Extended
/dev/hdc5            3578        3736     1277136   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    c  W95 FAT32 (LBA)

```
how do i make the NTFS one not bootable?

---

### Post by PeterJS on 2008-01-06
Looks like it's there to me, and has windows installed on it. Is windows not booting for you?

---

### Post by money2themax on 2008-01-06
> **PeterJS said:**
> fdisk is the command line partition editor and manager and the -l option tells it to list all the current partitions and then exit. In this case the sudo isn't needed unless you used bastile to lock your system down.

how do i lock it down

---

### Post by lisati on 2008-01-06
> **lisati said:**
> +1

> **lolzlolz said:**
> +1 wat do you mean???

Agreeing with you, friend, that it depends on if your system is set up to have something there....but we digress....

---

### Post by Rocket2DMn on 2008-01-06
Looks like sda1 is a partition of sda which is probably running windows.  hdc looks like your linux drive with its partitions.  sdb1 is the partition on sdb which looks like a drive you use for data (or a really old windows drive) since it has FAT32.
You have 3 drives, not 2!  Maybe one is external?  Or a USB flash drive?

---

### Post by money2themax on 2008-01-06
> **PeterJS said:**
> Looks like it's there to me, and has windows installed on it. Is windows not booting for you?
no windows isn't on it anymore i just keep it NTFS for 2 reasons 1 so i can switch it in to another computer that has XP and because i don't know how to reformat it

---

### Post by money2themax on 2008-01-06
> **Rocket2DMn said:**
> Looks like sda1 is a partition of sda which is probably running windows.  hdc looks like your linux drive with its partitions.  sdb1 is the partition on sdb which looks like a drive you use for data (or a really old windows drive) since it has FAT32.
You have 3 drives, not 2!  Maybe one is external?  Or a USB flash drive?

the Fat 32 is a WD 120GB passport USB

---

### Post by Rocket2DMn on 2008-01-06
You can reformat the drive to whatever you want by downloading and running "gparted" (will require sudo).  It's a great graphical program for managing drives and partitions.

---

### Post by money2themax on 2008-01-06
> **Rocket2DMn said:**
> You can reformat the drive to whatever you want by downloading and running "gparted" (will require sudo).  It's a great graphical program for managing drives and partitions.
gparted takes forever to load i let it be for 1 hour with no luck

---

### Post by Sef on 2008-01-06
> gparted takes forever to load i let it be for 1 hour with no luck

Get [GParted LIve CD]("http://gparted-livecd.tuxfamily.org/").

---

### Post by Rocket2DMn on 2008-01-06
OK, well here's a link that explains how to use the command line (fdisk) to partition if you want to use the ext3 filesystem on it: [https://help.ubuntu.com/community/InstallingANewHardDrive#head-3b50f4548d735e5249f97885af56acc5dfb0fe14](https://help.ubuntu.com/community/InstallingANewHardDrive#head-3b50f4548d735e5249f97885af56acc5dfb0fe14)
There are ways to format with other file systems as well.  Also the Gparted LiveCD -  [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by money2themax on 2008-01-06
> **Sef said:**
> Get [GParted LIve CD]("http://gparted-livecd.tuxfamily.org/").

cant i just get it to work from inside ubuntu?

---

### Post by Rocket2DMn on 2008-01-06
Try redownloading and installing it (it's available in the repositories)
```
sudo apt-get remove gparted
sudo apt-get install gparted
```
Then run it from the command line and post any output that might happen (like if there are errors), we can use that to help pinpoint a problem with it.
```
gksudo gparted
```

---

### Post by Sef on 2008-01-06
It's possible yes, just don't have that drive mounted.  But the GParted Live CD is more current than the one in Ubuntu.

---

### Post by money2themax on 2008-01-06
> **Rocket2DMn said:**
> Try redownloading and installing it (it's available in the repositories)
```
sudo apt-get remove gparted
sudo apt-get install gparted
```Then run it from the command line and post any output that might happen (like if there are errors), we can use that to help pinpoint a problem with it.
```
gksudo gparted
```
umm it gets to scanning all devices and won't continue

---

### Post by Rocket2DMn on 2008-01-06
Try unmounting the USB drive and the NTFS drive, then running gparted.  You can't modify the drives if they are mounted anyway.  Please post any command line output that appears.

---

### Post by money2themax on 2008-01-06
i can't unmount the 200GB HDD probly cuz it mounts automatically with the NTFS tool that i installed

---

### Post by Rocket2DMn on 2008-01-06
> **money2themax said:**
> i can't unmount the 200GB HDD probly cuz it mounts automatically with the NTFS tool that i installed

Yeah you can, just run
```
sudo umount /dev/sda1
```
If it's in your /etc/fstab file you can remount it later using
```
sudo mount -a
```

If you really can't get gparted to work in Ubuntu, then I would have to say use the GParted LiveCD.

---

### Post by money2themax on 2008-01-06
this is what happens [i don't have anything running]
```
umount: /media/Backup - Storage: device is busy
umount: /media/Backup - Storage: device is busy

```

---

### Post by Rocket2DMn on 2008-01-06
You can try to force the unmount by running
```
sudo umount -f /media/Backup
```
Otherwise, use the GParted LiveCD since you've been having trouble running it through Ubuntu.

---

### Post by money2themax on 2008-01-06
look at this
```
money2themax@MX-Ubuntu-000:~$ sudo umount -f /media/Backup
umount2: No such file or directory
umount: /media/Backup: not found
money2themax@MX-Ubuntu-000:~$ sudo umount -f /dev/sda1
umount2: Device or resource busy
umount: /media/Backup - Storage: device is busy
umount2: Device or resource busy
umount: /media/Backup - Storage: device is busy

```
i'm just gonna give myself root powers for a while

---

### Post by Rocket2DMn on 2008-01-06
Using sudo gives you root privileges to perform such administrative tasks as this.  I don't know why you can't unmount that directory (sorry for my mispelling, I missed the - Backup part), but try running gparted with the USB drive disconnected anyway (forget about the ntfs drive).  Otherwise, the only way I can see you getting this unmounting to work is to reboot the computer.  Let's just try the LiveCD since this isn't going anywhere.

---

