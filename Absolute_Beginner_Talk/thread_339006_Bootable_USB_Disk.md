---
title: "Bootable USB Disk"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Pobega on 2007-01-15
I've created a bootable USB Disk using syslinux and FeatherLinux 0.6*. It boots fine on my Windows systems, and runs smoothly. But for some reason it doesn't boot on computers with Linux already installed; When I go to my BIOS menu on bootup and select "USB Drive/Disk", it just bring me right into GRUB and Xubuntu.

I am probably missing something in my GRUB config, or maybe my BIOS so I don't know. I'm completely new to this, so I'm not sure where to even start.

---

### Post by yager on 2007-01-15
With your USB drive plugged in, start your computer and pull up your BIOS.

Check to see if you can boot from the USB drive directly.  Remember to put this drive as the first drive to check for a master boot record.  That should take care of your booting problem.

As a note, not all computers can boot from an USB drive.  Also, if you start the computer up at any time in the future with the drive unplugged, the BIOS will remove it as the first drive to check.

If you can not boot from the USB drive, you will need to configure GRUB's menu.lst file to call the USB drive.  You will need to modify the entry to something such as the following.

> title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

The root line will need set the drive number where the USB can be found.  Normally root is at (hd0,0) but hd0 is the drive that the MBR was found.  
Also check your device.  sda1 is most likely correct.
As for the kernel line, you will want to copy that from your bootable drive.

---

