---
title: "&quot;Error: Unknown filesystem grub rescue&quot;"
date: 2012-06-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dano2 on 2012-06-07
After replacing my entire Windows 7 OS with Ubuntu 10.04 on my Asus G73S, I've decided I want to dual-boot between the two. But after running the Windows Restore/Recovery Image (6 DVDs [http://dl.dropbox.com/u/80304796/b1.jpg](http://dl.dropbox.com/u/80304796/b1.jpg) ), I get "Error: Unknown filesystem grub rescue" ( [http://dl.dropbox.com/u/80304796/b3.jpg](http://dl.dropbox.com/u/80304796/b3.jpg) ). Any suggestions?

For what it's worth, here are my boot choices ( [http://dl.dropbox.com/u/80304796/b2.jpg](http://dl.dropbox.com/u/80304796/b2.jpg) ) and here is what "sudo fdisk -l" returns...

[PHP]
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c1d5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26214400    c  W95 FAT32 (LBA)
/dev/sda2            3264       27585   195354624    7  HPFS/NTFS
/dev/sda3           59489       60802    10543105    5  Extended
ubuntu@ubuntu:~$  
[/PHP]

---

### Post by dano2 on 2012-06-07
Please help. I have no idea where to go from here.

---

### Post by drs305 on 2012-06-07
Boot an Ubuntu LiveCD, download and install Boot-Repair, and let it fix your system for you. 

If it can't, it will give you the option to run the boot info script. Post the contents of RESULTS.txt and we may be able to see what is happening..

The boot repair link is in my signature line.

---

### Post by dano2 on 2012-06-08
> **drs305 said:**
> Boot an Ubuntu LiveCD, download and install Boot-Repair, and let it fix your system for you. 

If it can't, it will give you the option to run the boot info script. Post the contents of RESULTS.txt and we may be able to see what is happening..

The boot repair link is in my signature line.

Wow! That worked magically. Thanks tons.

---

