---
title: "Booting Linux from  external source"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by oldb0y on 2008-03-31
Have you tried setting BIOS to boot from usb?
Here is a good page: [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by ajgreeny on 2008-03-31
You can certainly install to a usb external drive, but I'm afraid the installation will then only run on the computer that you used to install it.  There is a way to run the usb drive as if it were a live CD so it will work on any machine, but I can't remember how it's done.  You will need to do a search of google and the ubuntu site for information.

---

### Post by carolus on 2008-03-31
Neither of my computers has a BIOS that supports booting from USB.  I can put Puppy Linux on a USB hard drive and boot it from a few small files on a boot CD, but I haven't seen any simple way to do that with Ubuntu that does not jeopardize my vendor-installed Windows by writing to the primary HD.

---

### Post by dstew on 2008-03-31
If you can boot the USB-connected hard disk, you can install Ubuntu on it and put the grub boot loader into the MBR of the Ubuntu hard drive. Then, put the USB port before the hard disk in the BIOS boot order. Ubuntu will boot when the drive is plugged in, but Windows will boot from the internal hard drive if it is not plugged in.

If your BIOS cannot boot the USB-connected drive, you can still install Ubuntu on it, but you will need to boot it from some other bootable source, like a bootable CD (the Ubuntu Live CD can be used) or a grub boot floppy.

---

### Post by bundleboy on 2008-03-31
>  I haven't seen any simple way to do that with Ubuntu that does not jeopardize my vendor-installed Windows 
What you can do is to try installing ubuntu in a computer with the primary partitions like how a normal installation would take place thereafter use Remastersys to "convert' this installation to a bootable iso. But it so happens you would need to sacrifice one HD
Source: [http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

> Neither of my computers has a BIOS that supports booting from USB.
You can try updating your bios if you are using american megatrends which most boards use look up this webbie for an update.
[http://www.ami.com/amibios/](http://www.ami.com/amibios/)

This is little i know hope it helps

Cheers :D

---

