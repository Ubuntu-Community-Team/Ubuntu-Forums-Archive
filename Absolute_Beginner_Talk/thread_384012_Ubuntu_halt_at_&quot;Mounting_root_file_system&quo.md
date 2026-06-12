---
title: "Ubuntu halt at &quot;Mounting root file system&quot;"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by hosammy on 2007-03-13
Hi, I am a newbie of ubuntu and just trying to shift my linux system from Fedora Core 6.

I burnt the ubuntu 6.06.1 DVD for i386, then I boot this live/install DVD from the DVD drive.
My current configuration:
IDE-0 Primary hda which installed with the ubuntu
SATA-0 sda which had installed the Windows XP with NTFS format.
SATA-0 sdb which store the Windows data with NTFS format.

The installation is completed. I reboot, then select: the "ubuntu, kernel 2.6.15-26-386"
The system halt at "Mounting root file system"

If I select the "ubuntu, kernel 2.6.15-26-386 (recovery mode)",
the system halt at: "[17179582.948000] ohci_hcd 0000:00:03.0: OHCI_HOST Controller"

Please advise ...:confused:

---

### Post by tgalati4 on 2007-03-14
Boot the Live DVD.

Mount hda.  (Use either the command line or the Disk Manager)  Be sure to designate a local directory as a mount point.

Share with us:

more /boot/grub/menu.lst
more /boot/grub/device.map

Check for any filesystem errors:

sudo fsck /dev/hda

---

### Post by grahams on 2007-03-14
I'm taking a wide guess here. but if it stops at ohci_hcd it may be hanging if you had a usb device connected during the install that isn't there anymore. Or maybe you've connected a usb device since you installed.

It may be the addition or removal of the device is making your root device /dev/hdb when it actually is expected at /dev/hda. If this seems likely try putting the hardware back to setup you used in the install and see if allows you to reboot. If so, take a look and /etc/fstab and see where it is mounting /

BTW. In 6.10 I think this type of issue gets fixed as IDs are written to partitions as metadata, so they can be moved (to some degree).

---

### Post by hosammy on 2007-03-15
Hi, 
I try to boot the live DVD again, however, it also halts at "Mounting root file system" no matter I boot the "start/install" , "safe mode" nor "text mode".

My config:
Main board: ASUS P4S8X-MX
1 gB RAM
1 11 in 1 usb card reader
1 DVD R/W
1 CD R/W
The HDD config are shown in my previous post.

Please advise:confused:

---

### Post by dstew on 2007-03-15
See post from grahams. Did you have your USB card reader connected when you installed the system?

---

### Post by Lexyboy on 2007-03-15
Try unplugging all non-essentials (USB, firewire etc.).  I had the same problem which turned out to be because I had my ipod plugged in, which Ubuntu apparently can't cope with (works fine once booted though).

---

### Post by hosammy on 2007-03-17
Reply dstew
The 11 in 1 usb reader is installed in the 3.5" slot replacing the 3.5" Floppy drive, ie. always connected.

Please advise...:confused:

---

### Post by dstew on 2007-03-17
That is an unusual device. Can you post the manufacturer's information about it? Name, model number etc.

Edit: Is it an Atech XM-4U?

---

### Post by hosammy on 2007-03-22
It is a "Magic-Pro 11-in-1 Internal Card Reader / Writer", the web is here:

[http://www.magic-pro.com/product/other/CardReader_Int.htm](http://www.magic-pro.com/product/other/CardReader_Int.htm)

Please advise ...:confused:

---

### Post by dstew on 2007-03-22
Is seems like it is looking for the root file system on your USB device. This could be because the kernel item for root is being misdirected to it by a mistake in your menu.lst file.

When you boot and see the Grub menu, enter the edit mode by pressing 'E' and see what the linux kernel line says.

---

### Post by hosammy on 2007-03-26
[COLOR="Blue"]When you boot and see the Grub menu, enter the edit mode by pressing 'E' and see what the linux kernel line says.[/COLOR]

Edit: [COLOR="Purple"]Ubuntu, kernel 2.6.15-28-386[/COLOR]
[COLOR="Red"]root (hd0,0)
kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-28-386
savedefault
boot
[/COLOR]

Edit: [COLOR="Purple"]Ubuntu, kernel 2.6.15-28-386 (recovery mode)[/COLOR]
[COLOR="Red"]root (hd0,0)
kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro single
initrd /boot/initrd.img-2.6.15-28-386
boot
[/COLOR]

Please advise...:confused:

---

### Post by dstew on 2007-03-26
That seems correct. I don't have any other ideas at present.

---

### Post by tgalati4 on 2007-03-26
Put Damn Small Linux on a memory card (choose one of 11 styles) and see if it will boot from the memory card reader.  I have to agree with the other responders, it seems like the card reader is causing a device mixup.  I assume this is a USB-connected card reader.  How difficult is it to disconnect?  Or, is there a BIOS setting to turn off?  

If you turn off USB in the BIOS, then you should be able to boot--or at least get farther in the boot process.

Let us know what works.

---

### Post by hosammy on 2007-03-26
I have just disabled the usb 11 in 1 cardreader but the problem persist.
Anyway, I will open thye PC's cover to disconnect this usb 11 in 1 cardreader.

However, I feel quite strange that this  usb 11 in 1 cardreader (with different brand name) is also installed in my office and my office's PC runs the ubuntu 6.10 quite smooth.

Is it the problem of the SATA-0 & SATA-1 HDD which the SATA-0 installed with the Windows XP system and the SATA-1 contains the Windows data, both are in NTFS format.

---

### Post by tgalati4 on 2007-03-26
Do you have any RAID configurations set in the BIOS?  Perhaps there is a RAID problem that is tripping up the boot process.

---

### Post by hosammy on 2007-03-27
[COLOR="Red"]Do you have any RAID configurations set in the BIOS? Perhaps there is a RAID problem that is tripping up the boot process.[/COLOR]

The mainboard is Asus P4S8X-MX.
The 2 SATA connectors connected to the 2 SATA HDD which store the Windows XP file, I set it in BIOS as "Native Mode", the others are "Disabled" and "RAID Mode"

:confused:

---

### Post by hosammy on 2007-03-27
After opening the PC's cover and physically disconnected the USB 11 in 1 cardreader, the boot process succeed and passed. I am upgrading to 6.10 and after that I will try to reconnect it again to see the effect.:)

---

### Post by actaris on 2007-03-27
I had the same problem with 6.10 but after a reset Ubuntu started usually. Every day, at morning:  halt at "Mounting root file system". Reboot and all go ok. If i do another reboot all ok. If I shut down the PC and start after 5 minutes there is the halt at "Mounting root file system" solved with the reset.
Now, whith ubuntu 7.04 beta the error message is segmentation fault but the behaviour is the same: start PC->lock->reset->all ok.
I have an usb hub, tomorroe morning I'll try to boot without the USB Hub.
tnx.

---

