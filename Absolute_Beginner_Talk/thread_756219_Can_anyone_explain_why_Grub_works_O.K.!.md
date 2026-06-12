---
title: "Can anyone explain why Grub works O.K.!"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-04-15
I've posted this about a month ago under a thread called "grub numbering" & it's still bugging me so I thought I'd try again. I tried Super Grub & after some number guessing
to finally got my dual boot with Gusty & XP to work. 
Everything is working O.K. but the more I learn about Grub the more I don't understand how my computer is working right booting either XP or Gusty.
Here goes:
3 internal HD's  = 2 ATA , 1 SATA 
(hda)Master ATA  160 gig>  OS - Windows XP  NTFS single partion
(hdb)Slave  ATA  160 gig>   OS - Ubuntu Gusty  - only
(sda)SATA  250 gig>  Fat32 - single partition used for audio files only

Grub will boot XP if its set to (0,0) in menu.lst which sounds right since its (hda)
but will only boot Gusty if set to (2,0) which is (hdb)
Even the output of my device.map:
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda
shows that Gusty should boot from (1,0)
I have a feeling its because I have a mix of ATA & SATA drives that's confusing Grub.
Has anyone ever seen or heard of a configuration like this or even have an idea what's going on with Grub here . Could this be a Grub bug?

Here's my menu.lst & fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92c092c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92819281

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005598e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       18700   150207718+  83  Linux
/dev/hdb2           18701       19457     6080602+   5  Extended
/dev/hdb5           18701       19457     6080571   82  Linux swap / Solaris

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-rt
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-rt
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro single
initrd          /boot/initrd.img-2.6.22-14-rt

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

---

### Post by Diabolis on 2008-04-15
If your music partition happens to be (1,0), then is just a matter of detection order. For some reason your drives are being recognized in this order: hda, sda, hdb.

If not, then I don't know.

---

### Post by garyed on 2008-04-15
You're obviously right in the order that grub is recognizing the drives but what doesn't make sense is the device.map is showing something different than what grub is recognizing.
I thought the whole idea of the device.map file was to show grub how to recognize the drives.

---

### Post by Diabolis on 2008-04-15
> what doesn't make sense is the device.map is showing something different than what grub is recognizing

I actually think that it makes sense. When your turn on your pc, the very first thing that is loaded is the bios, then the boot loader (grub) and after that the operating system of your choice. So device.map won't exist until you load linux.

---

### Post by garyed on 2008-04-16
> **Diabolis said:**
> I actually think that it makes sense. When your turn on your pc, the very first thing that is loaded is the bios, then the boot loader (grub) and after that the operating system of your choice. So device.map won't exist until you load linux.

Thanks for your input. This is very interesting & I'm tempted to do some experimenting. 
I see your point but the boot loader(grub) loads values from the menu.lst file before any operating system is chosen also. All I'm saying is that the values of the menu.lst file should 
be in sync with those of the device.map file even if it is not needed for boot-up. What I might do as a test is change the values of my device.map on a few different computers & see what effect if any they have on grub.

---

### Post by joe.turion64x2 on 2008-04-16
Perhaps that's the order the BIOS is instructed to boot devices from.

Usually, in the boot order sequence, there are only CD-ROM, HDD, Floppy, USB, Net, to choose from, but having more than one HDD, they should show up.

---

### Post by SnakeHips on 2008-04-16
Is it ignoring 
(hdb)Slave ATA 160 gig> OS - Ubuntu Gusty - only
(hd1) /dev/hdb

because it's set to "slave" ? Is GRUB working from drives set to "master" configuration?

---

### Post by garyed on 2008-04-16
Well after testing two computers I found that changing the device map has no absolutely no effect on Grub at boot-up. 

Those who mentioned bios settings were right as far as what Grub was seeing.
 When I looked at the order that my bios saw the HD's it would match the menu.lst order.
1 - ATA Master
2 - SATA
3 - ATA Slave

My guess is that the reason device.map is incorrect is beacause  Grub didn't  find the order the same as my bios & I had to edit  Grub at boot-up with the "e" command to get things working.  That didn't change anything in the device.map since it has no effect on Grub. It must be just a reference file for the user to relate to.

---

### Post by forrestcupp on 2008-04-16
[Here's a great read](http://forums.fedoraforum.org/showthread.php?t=153679) from the Fedora forums about device.map and grub.  It appears that device.map is not used in booting, but mainly for reinstalling grub.

---

### Post by Diabolis on 2008-04-16
That was a really good post at fedora forum. I think everything what he says is correct and from his conclusion I'll conclude:

device.map is used by grub and his developers, it is pointless to mess with it. If you have problems at booting your disks, do **sudo grub**. In that way it will probe devices and you'll fix the problem.

as stoat said:
> ... in the end, the device.map file itself doesn't make any difference in what occurs during the process of booting with the GRUB bootloader, and sometimes may even be a "red herring" unnecessarily complicating booting dilemmas when GRUB does not need to be reinstalled.

---

### Post by garyed on 2008-04-16
> ... in the end, the device.map file itself doesn't make any difference in what occurs during the process of booting with the GRUB bootloader, and sometimes may even be a "red herring" unnecessarily complicating booting dilemmas when GRUB does not need to be reinstalled.

That's exactly what I experienced ; both the "red herring" & that it has no effect on the boot process. That's what had me so confused. At least my mind's at rest now.<g>

---

### Post by adrian15 on 2008-04-18
> **garyed said:**
> That's exactly what I experienced ; both the "red herring" & that it has no effect on the boot process. That's what had me so confused. At least my mind's at rest now.<g>

Device.map is more important than you thing. When you update your Ubuntu installation, the kernel is update and the update-grub command is run which updates menu.lst. In order to get the linux drive - grub drive mapping it reads device.map.

So make sure that device.map is correct.

adrian15

---

### Post by forrestcupp on 2008-04-18
> **adrian15 said:**
> Device.map is more important than you thing. When you update your Ubuntu installation, the kernel is update and the update-grub command is run which updates menu.lst. In order to get the linux drive - grub drive mapping it reads device.map.

So make sure that device.map is correct.

adrian15

Very good point.

---

### Post by meierfra. on 2008-04-18
> In order to get the linux drive - grub drive mapping it reads device.map.

As far as I know  "update-grub" gets the linux drive from the "groot"-statement  in menu.lst. Only if there is no "groot" -statement in menu.lst (a very unlikely case)   the device.map is used.

---

### Post by adrian15 on 2008-04-21
> **meierfra. said:**
> As far as I know  "update-grub" gets the linux drive from the "groot"-statement  in menu.lst. Only if there is no "groot" -statement in menu.lst (a very unlikely case)   the device.map is used.

Indeed, you are right. I forgot the groot statement. However I ask myself if device.map is used in order to determine if map commands are needed to boot Windows or not. I actually do not know if Windows boot entry gets updated when a kernel update is done.

adrian15

---

### Post by meierfra. on 2008-04-22
> I actually do not know if Windows boot entry gets updated when a kernel update is done.

The windows entry does not get updated.  Kernel updates ignore everything outside the  "AUTOMAGIC KERNELS LIST" (And if the windows entry got moved to the " AUTOMAGIC KERNELS LIST" by accident, it gets removed.)

---

