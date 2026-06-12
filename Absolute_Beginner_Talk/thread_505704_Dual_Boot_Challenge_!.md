---
title: "Dual Boot Challenge !"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by ted70 on 2007-07-20
HI all

I cannot configure GRUB to boot XP and cannot configure NT BootLoader to start Ubuntu

I've read the stickies and can't find this particular problem

Any ideas greatly appreciated !

PS: I'm and experienced dos and windows user / developer, but a Linux nube

PPS: Really don't want to have to re-install windows again ! Just spent 3 days getting it back the way I like it.

Thanks in advance

I have a laptop with a single HD 
I installed Ubuntu Edgy (THANKS EVERYONE!) before Windows XP as follows:

	- booted from GParted Boot CD and partitioned disk with 4 partitions 
	(wiping everything there before)
	- installed Ubuntu onto the 1st partition - ok
	- 2nd partition formatted as NTFS for future Windows XP
	- 3rd used for linux swap
	- 4th fat32 shared data drive

Ubuntu booted fine from GRUB t this point

I then installed XP on the 2nd partition :
Of course the XP/NT Boot Loader took over the MBR and only allowed me to boot XP.

I can use the SuperGrub Boot CD to reinstall the XP/NT Boot Loader onto the MBR to boot Windows XP ok.
And I can use the same CD to reinstall GRUB onto the MBR which boots Ubuntu from GRUB ok.

But I cannot configure GRUB to boot XP and cannot configure NT BootLoader to start Ubuntu.
__________________________________________________________________________________________________________________________

When Grub is installed on the MBR I get 
"a disk read error occurred" 
when I try to boot to XP - see menu.lst below
(Ubuntu boots OK from Grub)
__________________________________________________________________________________________________________________________

When Windows XP/NT Boot Loader is installed on the MBR (using supergrub) 
- and after I have followed these instructions 
[www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=last&x-showcontent=text](www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=last&x-showcontent=text)

	# mkdir /mnt/share

	# mount -t msdos /dev/hda4 /mnt/share

	# dd if=/dev/hda1 of=/mnt/share/ubuntu.bin bs=512 count=1

	# ls -l /mnt/share

 

	shows ubuntu.bin with size 512 bytes.


	Now configure the Windows bootloader.

	Shut down the system and let Windows boot.

	Copy the ubuntu.bin file from the FAT32 Windows drive to drive C:\.

 

	Edit boot.ini add a new line at the end of the file:

	C:\UBUNTU.BIN="Ubuntu Linux"

I get error "invalid partition table" when trying to boot to Ubuntu from the XP/NT Boot Loader
(windows boots OK from the XP/NT Boot Loader)

[FONT="Courier New"]
__________________________________________________________________________________________________________________________
sudo fdisk -l 

Disk /dev/hda: 60.0 GB, 60011642880 bytes
16 heads, 63 sectors/track, 116280 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       20321    10241406   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/hda2   *       20321       81266    30716280    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/hda3           81266       81792      265072+  82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/hda4           81792      116280    17382330    b  W95 FAT32
Partition 4 does not end on cylinder boundary.

__________________________________________________________________
menu.lst

default		0
timeout		3

title           Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot



[/FONT]

---

### Post by bernied on 2007-07-20
I don't know how to use the windows bootloader, but this:
```
title Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0)
```will not work for a system with just one disk.

Those map commands are for a system with two disks. Try it without them.

---

### Post by davidjmayo on 2007-07-20
delete--didn't spot the map command

---

### Post by bernied on 2007-07-20
Try browsing the [grub manual](http://www.gnu.org/software/grub/manual/grub.html#map) to see what the map command does.

[Herman's dual boot site](http://users.bigpond.net.au/hermanzone/) is also very good for information.

---

### Post by gn2 on 2007-07-20
To set up a dual boot Windows Ubuntu dual boot from scratch, always start by installing Windows.
.
Boot the Windows CD.
.
Delete ALL partitions.
.
Create a partition the size you want for Windows and install Windows to it.
.
Leave free space!
.
Boot Ubuntu Live CD.
.
Click the install icon.
.
Install Ubuntu to the remaining free space on the drive setting the partitions as desired, (/, /home and swap)
.
Much more details in the Hermanzone link in my sig.
.

---

### Post by ted70 on 2007-07-20
Thanks Guys

solved by removing these from menu.lst as per your advice
map (hd0) (hd1)
map (hd1) (hd0)

now using the menu.lst below
(also upgraded to latest Ubuntu version and didn't have to re-install any OS)

Ubuntu is very nice indeed....:)

-------

default		1
timeout		3

title           Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=57edb578-7c92-4a1b-a5fb-b8505f525592 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=57edb578-7c92-4a1b-a5fb-b8505f525592 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

---

