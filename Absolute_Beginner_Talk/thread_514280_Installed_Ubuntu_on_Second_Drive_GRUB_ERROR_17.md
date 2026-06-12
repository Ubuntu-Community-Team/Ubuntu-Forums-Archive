---
title: "Installed Ubuntu on Second Drive GRUB ERROR 17"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by dylan623 on 2007-07-31
Hello, I installed Ubuntu (6.06, I think) to a second hard drive in my PC, but I installed GRUB to the the primary (XP) drive. After I removed the Ubuntu drive (there is only space for two drives, and I absolutely need to have two of the drives already in there, but soon I will able to use three), I was not able to boot XP. In order to fix this, I removed the MBR using the Windows installation disk. However, when I put the Ubuntu drive back in, I was not able to access it. I tried to reinstall GRUB, but I got fed up with it and just reinstalled Ubuntu. This time I installed GRUB on the Linux drive. But when I tried to go into the newly installed Ubuntu I got Error 17. I looked around on the forums for a while, but I was not able to find a solution to my problem. Could anyone help?

---

### Post by wolfen69 on 2007-07-31
you should have disconnected the xp drive while installing ubuntu. live and learn.

---

### Post by dylan623 on 2007-07-31
> **wolfen69 said:**
> you should have disconnected the xp drive while installing ubuntu. live and learn.

Do you have any advice as for what to do now, though?

---

### Post by annda on 2007-07-31
can you boot from live cd and access the external disk to see what /boot/grub/menu.lst file looks like and maybe post it here?

you can access the disk under windows too, you will need this driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

UPDATE: if you use the live cd, can you check the output of the command?

```
sudo fdisk -l
```

this will tell us more about your partitions and what they should look like in grub's menu.lst configuration file

---

### Post by dylan623 on 2007-07-31
> **annda said:**
> can you boot from live cd and access the external disk to see what /boot/grub/menu.lst file looks like and maybe post it here?

you can access the disk under windows too, you will need this driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

UPDATE: if you use the live cd, can you check the output of the command?

```
sudo fdisk -l
```

this will tell us more about your partitions and what they should look like in grub's menu.lst configuration file

No, my drives don't show up.:(

---

### Post by dylan623 on 2007-07-31
I forgot, these are the results of fdisk:

Disk /dev/hda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       48641   390708801    7  HPFS/NTFS

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2377    19093221   83  Linux
/dev/hdb2            2378        2482      843412+   5  Extended
/dev/hdb5            2378        2482      843381   82  Linux swap / Solaris

---

### Post by confused57 on 2007-07-31
> **dylan623 said:**
> Hello, I installed Ubuntu (6.06, I think) to a second hard drive in my PC, but I installed GRUB to the the primary (XP) drive. After I removed the Ubuntu drive (there is only space for two drives, and I absolutely need to have two of the drives already in there, but soon I will able to use three), I was not able to boot XP. In order to fix this, I removed the MBR using the Windows installation disk. However, when I put the Ubuntu drive back in, I was not able to access it. I tried to reinstall GRUB, but I got fed up with it and just reinstalled Ubuntu. This time I installed GRUB on the Linux drive. But when I tried to go into the newly installed Ubuntu I got Error 17. I looked around on the forums for a while, but I was not able to find a solution to my problem. Could anyone help?

If you get a grub boot menu when you boot first to your Ubuntu drive, highlight your Ubuntu enty, press "e" to edit, then highlight the line with root, press "e" again, change root from (hd1,x) to (hd0,x), press "enter", then "b" to boot...Note: x means leave this value as it is...this change is temporary if it works, but you can make it permanent in you /boot/grub/menu.lst.

---

### Post by dylan623 on 2007-07-31
> **confused57 said:**
> If you get a grub boot menu when you boot first to your Ubuntu drive, highlight your Ubuntu enty, press "e" to edit, then highlight the line with root, press "e" again, change root from (hd1,x) to (hd0,x), press "enter", then "b" to boot...Note: x means leave this value as it is...this change is temporary if it works, but you can make it permanent in you /boot/grub/menu.lst.

Ok, I will try that in a minute. I'll get back to you afterwards, preferably in my new installation.

---

### Post by dylan623 on 2007-07-31
Thanks, everything works fine now. Now I only have bigger problems to fix in Windows...

---

