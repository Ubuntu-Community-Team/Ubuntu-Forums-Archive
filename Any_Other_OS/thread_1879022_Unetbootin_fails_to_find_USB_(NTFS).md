---
title: "Unetbootin fails to find USB (NTFS)"
date: 2011-11-10
forum: Any Other OS
---

### Post by gnush on 2011-11-10
Hello!

I'm triyng to make a bootable USB with unetbootin, the USB has been formatted with NTFS as that is required. The problem is that the USB doesn't show up in unetbootin (I can mount it and see it in fdisk).

What's causing this? Do I need some additional libraries?
I'm on Fedora 15, if that makes a difference.

Thanks in advance.

---

### Post by coffeecat on 2011-11-11
> **gnush said:**
> I'm triyng to make a bootable USB with unetbootin, the USB has been formatted with NTFS as that is required.

Are you sure? The few times I've used unetbootin I've formatted the pendrive FAT32. Indeed:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

> If your USB drive doesn't show up, reformat it as FAT32.

---

### Post by gnush on 2011-11-13
> **coffeecat said:**
> Are you sure? The few times I've used unetbootin I've formatted the pendrive FAT32. Indeed:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Thanks for answering; however, I'm pretty sure it needs to be NTFS as it's Windows. And I'm pretty sure I've actually successfully installed Windows with a USB using Unetbootin.

Fat32 doesn't work in the sense that the Windows installer isn't booted.

---

### Post by kurt18947 on 2011-11-13
Perhaps the confusion is this.  Which O.S. are you trying to install on the flash drive, Linux or Windows?  I thought Unetbootin creates only Linux live installs, not Windows live installs. 
Do you have a Windows install CD or DVD?  If so, perhaps you could unplug any internal drives and try to create a 'normal' windows installation on the USB drive.  I don't know if it'd work or not.

---

### Post by gnush on 2011-11-13
> **kurt18947 said:**
> Perhaps the confusion is this.  Which O.S. are you trying to install on the flash drive, Linux or Windows?  I thought Unetbootin creates only Linux live installs, not Windows live installs. 
Do you have a Windows install CD or DVD?  If so, perhaps you could unplug any internal drives and try to create a 'normal' windows installation on the USB drive.  I don't know if it'd work or not.

I'm trying to install Windows on the USB. And it has worked before, so I don't understand why it shouldn't work now.

Using a CD/DVD is impossible at this moment as I don't have any CD/DVD readers; I only have an image of Windows.

---

### Post by osfight.de on 2012-01-09
Unetbootin does indeed [create Windows Live CDs]("http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/"), however for Win 7 you must format the pendrive with NTFS. The unetbootin version installed in Ubuntu 11.10 does not detect NTFS drives, but I used build 494

[http://sourceforge.net/projects/unetbootin/files/UNetbootin/494/](http://sourceforge.net/projects/unetbootin/files/UNetbootin/494/)

Make sure to set the "executable" option under file>properties when you did download the file and that you click on "show all devices" when you executed the program. Make sure that you know what /dev device is your usb stick, e.g. using Gparted!

---

