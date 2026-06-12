---
title: "Can't Install Windows 8"
date: 2012-10-27
forum: Any Other OS
---

### Post by rajiv1096 on 2012-10-27
Hello all, I'm having trouble deleting ubuntu (dont' worry, I have it installed on other computers) and installing Windows 8. I'm installing via USB (no cd drive), and everytime I try to install setup says "Setup could not create a new system partition". I've deleted all partitions, and the same thing happens. I attached a screenshot of my partitions. Any help would be great. Thanks!

---

### Post by oldfred on 2012-10-27
You did not delete the extended partition which is taking up most of the drive.

Windows only installs to a primary (sda1 thru sda4) NTFS formatted partition with the boot flag or you have to have an available primary partition and space for Windows to create its own primary partition(s). Normally Windows 7 & 8 create two partitions, one a small 100 or 200MB hidden boot/repair and the rest as the main or c: drive partition. This is all with BIOS/MBR systems. 

UEFI with gpt partitions are different.

---

### Post by Bucky Ball on 2012-10-27
*Thread moved to **Other OS/Distro Talk***

---

### Post by rajiv1096 on 2012-10-27
So how would I go about deleting the extended partition? Through windows setup?

---

### Post by critin on 2012-10-27
> **rajiv1096 said:**
> So how would I go about deleting the extended partition? Through windows setup?

That- if it will, or gparted with a live iso,    I would also delete the small partition there.  Start clean.

---

### Post by rajiv1096 on 2012-10-27
> **critin said:**
> Yes.  I would also delete the small partition there.  Start clean.

I've done this several times, but I still get the same error..

---

### Post by critin on 2012-10-27
> **rajiv1096 said:**
> I've done this several times, but I still get the same error..

Is there an error in gparted?  What does it say?

your disk is encrypted.  Click on the red mark beside sda/5 and see what it  says.  The red mark may simply belong to encrypted disks, I don't use them so don't know. I've seen errors show like that though.

---

### Post by MikeCyber on 2012-10-28
Probably easiest would be to do it through windows install? There should be an option to use/erase all disc etc.
Personally I've Win8 on sda7 and am booting with Grub also Vista/Osx86/Ubuntu10.04 and 12.10 etc.
Very easy nowadays to multiboot tons of OS.

---

### Post by critin on 2012-10-28
Since he doesn't have an operating system installed, wouldn't he have to get rid of the encrypted issue before he can use the disk?

Isn't it normally encrypted** after **installing the system?  (I've no knowledge of this--learning)

---

