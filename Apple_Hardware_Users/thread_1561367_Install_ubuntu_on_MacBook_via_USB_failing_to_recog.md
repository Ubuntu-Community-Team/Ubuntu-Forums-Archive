---
title: "Install ubuntu on MacBook via USB: failing to recognize bootable USB"
date: 2010-08-26
forum: Apple Hardware Users
---

### Post by epb on 2010-08-26
Hi,

I have a MacBook on which I would like to install ubuntu from a USB drive. I followed the instructions on [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and have successfully created what seems to be a bootable USB drive. But when I restart, holding down the alt-key, my computer does not seem to recognize the usb drive as bootable (only my harddisc is displayed on the choose-startup-drive-screen. What could be wrong? I am using an Intel Mac with OS X 10.6.

Regards

---

### Post by Taoye on 2010-08-26
Intel Macs only support booting from USB devices that are formatted with the GUID partition table (GPT), and I think it follows that said USB stick needs to contain an EFI bootloader such as grub-efi. Hope that helps.

---

### Post by epb on 2010-08-26
Thanks for your response. As I mentioned I have been using the standard ubuntu-install method found at the URL above. The commands I run during this, does not seem to use the GUID-partition scheme to partition my USB drive. Can I alter the commands to do that? It is possible for me to set the partition using the DiskUtil.app but the partitioning is removed when I run the commands....

I am not sure what you mean when you say that I need a bootloader on the drive...?

---

### Post by srs5694 on 2010-08-26
You could use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to convert the USB disk from MBR to GPT format after you put the image on it. (A version is available for OS X, so you can do it from your existing OS.) I doubt if that alone would make it bootable, though, and I'm not sure what you'd need to do to make it so.

To answer your question about boot loaders, a boot loader is software that directs the boot process to a particular partition or kernel. The EFI firmware on Intel-based Macs has its own built-in boot loader, but it is of course intended to boot OS X from GPT disks. Since the USB disk image you've got is (presumably) designed for MBR and BIOS rather than EFI, it lacks the hooks needed to get Apple's EFI boot loader to work. Boot loaders such as rEFIt and GRUB 2 have EFI modes that enable them to interface with Apple's boot loader, but it's doubtful they're set up on that disk image in such a way as to make booting from the USB drive work right off the back on your system.

---

### Post by epb on 2010-08-26
It sounds like it is very cumbersome to install on Ubuntu on a Mac using an USB-drive... :( Does anyone know a place where this installation process is explained in more detail? Because it seems to me that the official guide is incomplete. I know they recommend you to do the installation using a CD, but my problem is that the CD-drive in my Mac is broken :(

Anyway, if nobody has a better idea I might try using gdisk, but I am not sure what to do with the bootloader.

---

### Post by linuxopjemac on 2010-08-27
[http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=88](http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=88)
[http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick](http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick)

---

