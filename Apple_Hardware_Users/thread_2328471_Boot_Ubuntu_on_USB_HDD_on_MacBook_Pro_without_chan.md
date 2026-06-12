---
title: "Boot Ubuntu on USB HDD on MacBook Pro without changing Mac system"
date: 2016-06-21
forum: Apple Hardware Users
---

### Post by grant-wq on 2016-06-21
I have a MaccBook Pro with a 128GB SSD. I am trying to install Ubuntu 16.04 on a USB HDD. I really don't want to make any changes to the Mac system itself, including the Mac bootloader or boot manager.

Since I can boot from a USB stick easy enough - simply holding down ALT after the boot chime - I figure I should be able to make a USB HDD bootable in a similar manner, in as much as there's no changes to the existing Mac system, and I simply hold down the ALT key during startup to boot from the USB HDD.

Booting from the USB stick is fine. I can run through the installer, make the USB HDD a GPT disk, create the partitions in any way that I need to... but what to do about "installing the bootloader" so I can actually use the system?

It doesn't seem to matter if I select the disk itself (/dev/sdc in this instance) or the ~200MB EFI partition (/dev/sdc1 in this instance) - neither option gives me a bootable USB drive, which leads me to believe that perhaps this isn't going to be as straight forward as I had thought.

I'm more than happy to pump in some command line love to get this working, I'm certainly not new to Linux systems but I have near zero experience with U/EFI systems, so this is kinda new to me.

My ideal scenario is to have a USB HDD with Ubuntu installed on it where my Mac knows nothing about it at all and to boot it I need to hold the ALT key during startup. I'm not concerned about having a pretty graphical boot - hell, LILO in the late 90s was hardly pretty, so I'm sure I can cope.

---

### Post by oldfred on 2016-06-21
I assume a Mac has same issue as PC, but do not know Macs.

Ubuntu's grub in UEFI mode only installs to the ESP - efi system partition on sda.
And UEFI only boots external devices from /EFI/Boot/bootx64.efi on ESP on external.
So you have to copy /EFI/ubuntu from sda to sdc and copy again to /EFI/Boot and rename shim or grub to bootx64.efi. You have to have both as grubx64.efi is hard coded to look for more files in /EFI/ubuntu.

       [http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)
[http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 
   Mac with NVMe
[http://ubuntuforums.org/showthread.php?t=2274095](http://ubuntuforums.org/showthread.php?t=2274095)
EFI partitions: Also some info on efi partition on a Mac.
[URL="http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi"]http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi
[/URL]
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 

[URL="http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi"]
[/URL]

---

### Post by grant-wq on 2016-06-21
Thanks, OldFred.

So, just to clarify:
1) Boot from USB Stick.
2) Run installer.
3) Make USB HDD a GPT disk, add "EFI System" as first partition, then Ext4 and Swap after.
4) Install onto USB's Ext4 partition.
5) Install GRUB to USB's "EFI System" partition (sdc1)
6) Manually copy files into place so GRUB finds them.
7) Reboot, holding ALT and pray to the penguin gods.

---

### Post by sudodus on 2016-06-21
Welcome to the Ubuntu Forums :-)

I have made an installed system, that can boot from a USB drive (pendrive, SSD or HDD) in UEFI mode as well as in BIOS mode. It works in PCs, but I don't know if anyone has tested it in a Mac computer yet. So you might be the first one to try it in a Mac. See the following links,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[Installation/UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)

[Another new, simpler and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13468260#post13468260)

[Two updated compressed image files are uploaded](http://ubuntuforums.org/showthread.php?t=2213631&page=8&p=13494760#post13494760)

You can install this system with [mkusb](https://help.ubuntu.com/community/mkusb), which uses the cloning method, and 'everything' will be installed to the correct drive, including the bootloader. Afterwards you can move (and expand) the swap partition and after that expand the root partiition to use as much of the external drive as you like.

But notice that the current partition table will be overwritten, so you should copy all important files from the target drive to somewhere else.

---

### Post by grant-wq on 2016-06-23
OK, I'm making some progress - I decided that rather than get the USB HDD to boot the way a "normal" HDD install should do so, I'm making it boot the way the USB Stick boots: by using SysLinux. A bit of tweaking will be required, and maybe even throwing together my own initrd, but it's getting there.

---

### Post by oldfred on 2016-06-23
The Ubuntu installer uses Syslinux for BIOS boot and grub for UEFI boot. 

It has the /EFI/Boot/bootx64.efi which is another version of grub with only the files it needs to boot installer in /EFI/Boot.

Syslinux is in MBR for BIOS boot.

---

### Post by grant-wq on 2016-06-23
Aaaah! That might explain why the changes I just made to the syslinux config file on the USB HDD didn't show up just now when I tried again.

It would seem that things are a fair bit different to when I rolled my own LinuxFromScratch on x86-32 in the early 2000s. This is one big ol' learning experience and I'm loving it!

---

### Post by oldfred on 2016-06-23
I just did an install of Yakkety to my sdb drive on my PC. 
And specifically told it to install grub to ESP on sdb. And it said during install "installing grub to sdb". But it overwrote my main working install's grub in ESP on sda. But having learned it always does that, I have a copy of grub.cfg in /EFI/ubuntu to copy back.

---

