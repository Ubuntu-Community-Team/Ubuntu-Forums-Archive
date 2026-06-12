---
title: "[SOLVED] GRUB error 22 after editing menu.lst"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by LegeDoos on 2007-09-07
Hi there!

I'm new in this Ubuntu thing and installed Ubuntu on mij PIII800. I use 3 primary partitions (WinXp, W2K3, empty), 1 extended where I installed Ubunto. Everything went ok. I started editing menu.lst to make things work for WinXP and W2K3. I added commands like hide (hd0,1) etc. When I rebooted GRUB said that the partition doesn't exist followed by GRUB error 22. When I reboot again, I get error 22 right away.

I want to fix these errors but I don't know how to get to the menu.lst file. I started the live CD, but now I can't find menu.lst. Probably I have to mount the drive? Can anybody help me?

Regards,

LegeDoos

---

### Post by justleen on 2007-09-07
your well on your way..

boot from the live cd and them mount your ext3 partition
in a terminal:
```
 sudo fdisk -l 
```
this will tell you what device you need - its the ext3/linux filesystem.
for example:
/dev/sda6            1175        1238      514048+  83  Linux

make  a dir to mount on
```
 sudo mkdir /media/disk 
```

mount
```
 sudo mount /dev/sda6/ /media/disk 
```

you can now open the menu.lst
```
 gedit /media/disk/boot/grub/menu.lst 
```

---

### Post by Sef on 2007-09-07
GRUB error:

> 22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

---

### Post by LegeDoos on 2007-09-07
Thnx! That's what I needed. Only problem is that I just f*cked up my partition table, so I can start all over again :-(

---

