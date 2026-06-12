---
title: "Grub Error 15"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by cogvos on 2008-02-27
Dear all,

Grub has just gone belly up on me and have no idea why! I have a dual boot system Linux and Windoz XP. 

Linux is on a sata disk which is listed as the second in the BIOS (the first being the XP PATA disk)

I boot by bringing up the bios boot menu and selecting the sata drive. So this is now the 1st drive and grub is installed on this drives MDA (or whatever those 1st sectors are called). In effect it's as if Windoz is not connected at boot.

My brother needed a USB drive  repartitioned so I plugged it in and fired up windowz and partion magic 8. All went OK, but now when I try to start UBUNTU I get grub error 15! Huh? how is this possible? USB disks are listed after PATA and sata disks in the bios! How can partitioning a USB drive in windoz stuff grub on a totally different drive, particularly when the USB drive is now not connected! :confused:

Also how on earth do I fix it?

The drives are partitioned as follows:
In Windows partition magic they are listed thus;

Disk 1: Windows K: | Linux Swap | linux Root | Home | Windows F: (all in an extended partion)
Disk 2: windows Q: | Linux 6.4 | Linux Swap | Windows swap (all extended again)
Disk 3: Windows D: | Windows C (master partions, or whatever they are called)

To confuse matters bios lists the disks as follows

CH1 M PATA - Disk 3 in the above
CH3 M sata - Disk 1 in the above
CH4 M sata - Disk 2 in the above

Ignoring  the fact that I have 2 swap partions I want grub to pick up the root on Disk 1, 2nd partition in the extended block. I think this is HD (0,6) ? Am I right? How do I find out where grub is looking? 

I have an UBUNTU install dvd so Ican boot. But...
How do I mount the root partition I want to look at
Where do I look?

And to think all I wanted yesterday was a nicer trash can!

J
PS Please don't ask why I don't just use grub as a boot loader for Linux and windoz it's too complex and I'll cry...

---

### Post by Duck2006 on 2008-02-27
From the live CD in the terminal type

sudo fdisk -l

and post the output so we can see witch disk has what on it.

---

### Post by cogvos on 2008-02-27
OK here it is 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4485e66d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sda5               2        5101    40965718+   7  HPFS/NTFS
/dev/sda6            5102        5709     4883728+  82  Linux swap / Solaris
/dev/sda7            5710        7168    11719386   83  Linux
/dev/sda8            7169       10933    30242331   83  Linux
/dev/sda9           10934       60801   400564678+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x021fe081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        9733    78172290    f  W95 Ext'd (LBA)
/dev/sdb5               2        4868    39094146    7  HPFS/NTFS
/dev/sdb6   *        4869        8499    29165976   83  Linux
/dev/sdb7            8500        8761     2104483+  82  Linux swap / Solaris
/dev/sdb8            8762        9733     7807558+   7  HPFS/NTFS

Disk /dev/hda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         832     6289888+   c  W95 FAT32 (LBA)
/dev/hda2   *         833       20672   149990400    7  HPFS/NTFS

Disk /dev/sdc: 2063 MB, 2063597056 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         251     2015200    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(249, 254, 63) logical=(250, 225, 38)

The last is a usb memstick, it does not boot with this in or out!

I had a look in boot/grub and found the menu list, but could not edit/save it as I did not have permissions to do so when I booted from the live disk. And I cannot log in as root since I have no idea what the password for root is on a 7.10 live disk.. Help!?

J.

---

### Post by Duck2006 on 2008-02-27
Try

cat /boot/grub/menu.lst

and post the output.

---

### Post by cogvos on 2008-02-28
I can do so, but I'm not sure if this will help, since grub is failing before the menu list is displayed, rather than after. It looks like it can't find grub 2 which is, I think the bit that loads the list?

On the screen I have 

Grub 1.5

Error 15

J.

---

### Post by Duck2006 on 2008-02-28
> **cogvos said:**
> I can do so, but I'm not sure if this will help, since grub is failing before the menu list is displayed, rather than after. It looks like it can't find grub 2 which is, I think the bit that loads the list?

On the screen I have 

Grub 1.5

Error 15

J.


I will help, it will show as to where grub is been pointed to to load the OS and if that is wrong then it will not point to the wright partition.

---

### Post by cogvos on 2008-02-29
Many many thanks for all your posts. I eventually solved the by reinstalling grub. I found a very good how to here [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) which lead me through the process.

For those who are interested, I first disconnected the windowz drive completely. Then booted into the live DVD and followed the instructions above.

find /boot/grub/stage1

told me that boot was in hd (0,7) and hd(1,5) - as I have two linux installs. 

I typed root (0,7) and then setup (hd0) **this was ok for me as I had grub installed onto the MBR make sure you  read all of [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)  if you already have a boot loader there! otherwise you will overwrite it!**

Anyway booting after this got me to the grub menu screen, but then I got error 15, file not found when I selected linux. I had to change the root in the menu list to (0,6) to get it to work (why???)

Editing menu.lst (after finding out how to get permissions to do so!) fixed the problem and I am back on Linux. phew...

So once again many thanks for your help and suggestions.

J.

---

