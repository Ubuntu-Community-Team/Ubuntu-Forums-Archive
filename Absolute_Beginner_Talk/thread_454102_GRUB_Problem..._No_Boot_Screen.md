---
title: "GRUB Problem... No Boot Screen"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by arunmvishnu on 2007-05-25
Hi.. last week i got Ubuntu 7.04 cd and i installed it my new machine (Intel core 2 duo 6300, 1GB RAM, Intel 946Mobo). i Have 2 harddisk, 120GB sata and 80GB IDE.. i installed ubuntu in my 80GB disk without connecting 12gb hdd.After successful installation i got the message to reboot the system. After rebooting iam getting a error message that no bootable device is found. I checked boot priority and all such settings and gave first priority to this harddisk. Hard disk is working fine and i can boot to my vista or xp by connectiong sata disk. I installed it 2 times and iam getting the same error message. Installed partition is the primary partition with 10gb space. I gave 850Mb as swap space. 



buntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1197 1305 875542+ 82 Linux swap / Solaris
/dev/sda2 1306 9729 67665780 f W95 Ext'd (LBA)
/dev/sda3 1 1196 9606838+ 83 Linux
/dev/sda5 1306 1958 5245191 7 HPFS/NTFS
/dev/sda6 1959 3916 15727603+ 7 HPFS/NTFS
/dev/sda7 3917 6527 20972826 7 HPFS/NTFS
/dev/sda8 6528 7441 7341673+ 7 HPFS/NTFS
/dev/sda9 7442 9729 18378328+ 7 HPFS/NTFS




I installed GRUB and tried to boot, But iam getting the same error.. NO bootable device is found..

grub> find /boot/grub/stage1
(hd0,2)

grub> root (hd0,2)

grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


Please help me..

---

### Post by Borzo on 2007-05-25
According to your fdisk -l your linux partitionis not set up as bootable. set it as bootable with cfdisk, restart and see what happens.

---

### Post by Terl on 2007-05-25
I take it you want to manually change which disc the pc is booting from?  If so, if ubuntu is on the 80 gig hard drive I would put grub on the mbr of that drive hd0,0.  You have it on hd0,2.

---

