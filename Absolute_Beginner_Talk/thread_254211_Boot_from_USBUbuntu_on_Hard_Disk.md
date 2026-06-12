---
title: "Boot from USB/Ubuntu on Hard Disk?"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by silverjim on 2006-09-09
Afternoon.
This is what I'd like to do:

If I don't have a USB stick in one of my USB ports, boot into Windows.

If I do, then boot into Ubuntu BUT have all the files, etc. on my hard drive.

I'd like to do it this way because I don't want to go through the dual-boot menu everytime I boot up. 

I'd rather not run the LiveCD or have the Ubuntu files on the USB stick - just the ones needed to boot up Ubuntu and then switch control to the hard drive. Is this possible? Or is there a better way to do this? Thanks.

silverjim

---

### Post by jorn on 2006-09-09
There is a SMB = Smart Boot Manager on the install cd in cd/install/smb.bin.
You can put that onto a floppy if you have got one, or maybe to your stick.
The floppy is a part of the boot priority on my pc but not an USB device.
You can also put the bootloader grub on a floppy or maybe USB stick.
Just some thoughts.
If your BIOS has got a setup where you can chose boot device with few clicks that would be easiest.

---

### Post by edm1 on 2006-09-09
why not alter /boot/grub/menu.lst to set windows as the default OS, and set the timeout to a few seconds, so it would barely bother you. Surely that would be easier than having to find a usb pen everytime you want to boot ubuntu.

---

### Post by silverjim on 2006-09-09
Ah! I didn't know you could set the boot selection timeout(I fear that things GRUB and Linux are nearly beyond my meager knowledge at this time). I think that I shall proceed with my plans of partitioning off about a 10gb segment of my hard disk (Dell Inspiron 9200 w/80gb disk) and play with Ubuntu. Many thanks.

silverjim
accept no substitutes

---

