---
title: "Add hard drive - lose sharing?"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by AwesomeSpaceMonkey on 2007-08-29
I have a Ubuntu PC networked to 2 Windows computers.  Everything was working fine and I went to add a new HDD to the Ubuntu computer.  I followed the directions at

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

formatted the drive to fat32 with GParted, and added the following line to /etc/fstab :

/dev/sda1   /backupdrive   vfat   user   0   0

The new drive is SATA and the boot drive is PATA so I think it is listed as /dev/hda1.

The drive seems to be fine and when I check the size of the /backupdrive folder it is the size of the new drive.  The problem is that I can no longer see the shared Ubuntu drives from Windows.  I can browse from Ubuntu to Windows but not the other way around.  The Windows PC sees the Ubuntu box on the network but says it can not connect.  If I remove the new drive on the Ubuntu box, all sharing is fine.  I'm really new to Ubuntu and would appreciate the help.  Thanks.

---

### Post by GMachine_24 on 2007-08-30
Hi:

I don't believe I know the answer to your problem immediately here. But I was wondering why you formatted the drive as FAT32 instead of ext3 or whatever .... the Linux format .....?? Perhaps is you use the Linux format it will resolve your problem ....

I have found it much easier to use command line instructions to partition and format a drive  than a program such as you used.....



gm

---

### Post by AwesomeSpaceMonkey on 2007-08-30
I figured it out.  The boot drive was added on the second SATA channel and when it was by itself it was listed as sda.  When I added the new drive it was on the first SATA channel so it became sda and the boot drive became sdb.  This caused the sharing to be messed up.  By simply switching the SATA ports the boot drive went back to sda and the new drive is sdb and sharing works fine.  BTW the reason the new drive is fat32 is because I want to use it as a backup and I figured it would be easier to recover the data from a windows machine if I ever needed to.

---

### Post by GMachine_24 on 2007-09-01
I figured it out.  The boot drive was added on the second SATA channel and when it was by itself it was listed as sda.  When I added the new drive it was on the first SATA channel so it became sda and the boot drive became sdb.  This caused the sharing to be messed up.  By simply switching the SATA ports the boot drive went back to sda and the new drive is sdb and sharing works fine.


>   BTW the reason the new drive is fat32 is because I want to use it as a backup and I figured it would be easier to recover the data from a windows machine if I ever needed to.

Ok, just curious. I know Linux can format a hd as FAT32 but even when I format drives using a Windows format I use NTFS - which, admittedly, is more difficult to set up on Linux . . . but all my recovery software is for NTFS drives.

Hopefully you won't need it, right? I have had to replace so much hardware this summer because of incessant thunderstorms ... I think I have replaced the main drive on every computer but one (that would be five) and not counting laptops. And, of course, the UPC back ups too. I hate hate hate our local power company.

I had confusion with drives on a Kubuntu machine that has one main IDE drive and then two additional drives attached via a PCI RAID card - which on Ubuntu machines recognizes the drives in the hd* he* series but on Kubuntu recognize them as sd* drives. So I had to redo the fstab file but all ended well.

--gm

---

### Post by GMachine_24 on 2007-09-01
sorry... double entered the last post somehow

---

