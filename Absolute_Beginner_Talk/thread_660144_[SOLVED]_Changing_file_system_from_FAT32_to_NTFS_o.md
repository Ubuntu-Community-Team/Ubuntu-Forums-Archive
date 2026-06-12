---
title: "[SOLVED] Changing file system from FAT32 to NTFS on a dual boot machine"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by kamumosp on 2008-01-06
Hi,
I have Windows XP and UBUNTU 7.1 installed in my machine. I have one drive shared between these two OSes. My shared drive's file system is FAT32 and I want to change it to NTFS. Somebody please assist me how I can do that.

My partition table entries are as follows:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05b58753

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2196    17639338+   c  W95 FAT32 (LBA)
/dev/sda2            3854        7295    27647865    c  W95 FAT32 (LBA)
/dev/sda3            2197        2272      610470   82  Linux swap / Solaris
/dev/sda4            2273        3853    12699382+  83  Linux

Partition table entries are not in disk order

sda1 - Windows XP - FAT32
sda2 - shared        - FAT32
sda3 - swap          - swap
sda4 - Ubuntu        - ext3

Thanks
kam

---

### Post by mikewhatever on 2008-01-06
Try this [http://support.microsoft.com/kb/307881](http://support.microsoft.com/kb/307881)

---

### Post by geirha on 2008-01-06
Not sure of any programs that will convert FAT32 to NTFS in ubuntu (without reformatting), but I think Windows XP has some tool to do that (and it's probably safer to do it in windows anyway). 

It's a long time since I've tried windows xp, but I think you'd go to Control Panel -> Computer Management -> Drive Management or something like that.

EDIT: No, do what mikewhatever says ;)

---

### Post by barrack on 2008-01-06
Make sure that the drive you want to change is unmounted.

Install gparted and run gparted. 

It's a decent program. Easy to use.

It would require reformatting the drive, so back up all files that you have on it.

---

### Post by bodhi.zazen on 2008-01-06
You need to format the partition. Doing so will destroy all the data on the partition, so you will need to backup.

From Ubuntu you can use gparted to format or the command line.

gparted : sudo apt-get install gparted.

Unmount the partition and format.

command line :

mkntfs /dev/sda1

---

### Post by kamumosp on 2008-01-06
Hi all,
Thanks for your immediate reply.
I have one more question. If i convert the file system from windows, does ubuntu recognize  the converted drive (without losing any data).

Thanks
kam

---

### Post by geirha on 2008-01-06
Is the partition listed in /etc/fstab? if so, what does the line look like? if the filesystem-type is set to vfat (in fstab), ubuntu will fail to mount it untill you change it to ntfs-3g, otherwise there shouldn't be a problem.

That is, as long as you use the windows convert tool which should convert without deleting the files. Though it's a good idea to take a backup of the files if you can't afford to lose them. Just in case.

---

### Post by kamumosp on 2008-01-06
Hi,
I will convert my shared drive filesystem from FAT32 to NTFS (from Windows) and change fstab entry to ntfs-3g. I will update you with the status once I am done.

Thanks
kam

---

### Post by kamumosp on 2008-01-06
Hi,
I converted my shared drive filesystem to NTFS (from Windows) and could mount from Ubuntu. I did't have to format my shared drive for this.

Thank you all
kam

---

### Post by mikewhatever on 2008-01-08
> **kamumosp said:**
> Hi all,
Thanks for your immediate reply.
I have one more question. If i convert the file system from windows, does ubuntu recognize  the converted drive (without losing any data).

Thanks
kam

No, probably not. You'd have to remount the converted partition yourself.
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

