---
title: "EFI Boot - possible from flash USB install disk, but not  after installation"
date: 2011-05-08
forum: Apple Hardware Users
---

### Post by ivarss on 2011-05-08
Hi there.
I wonder what's so special about installation disk that iMac recognizes it at boot time even though installation is on MBR partition table? :confused:

[IMG]http://shpokas.files.wordpress.com/2011/05/efiboot.png?w=300&h=209[/IMG]

But why after installation I cannot select my external USB disk as boot choice? Note, this is different external USB disk that one used for installation.

In other words, I want to install Ubuntu on external USB disk and be able to select it as boot choice after installation.

Details:
Hardware - Intel iMac9,1 (Early 2009 Core 2 Duo).
Distro - Ubuntu Natty 64-bit
Boot disk created on USB flash from 64-bit ISO with Startup Disk Creator.

iMac recognizes installation on USB flash instantly at boot, offers "EFI Boot" entry if Option key is pressed.
After Ubuntu is installed on external USB disk, it is NOT recognized as bootable, no matter if MBR or GUID (GPT) partition table was chosen. Tried both.

Right now I boot Ubuntu on iMac through rEFIt boot CD or modified grub.cfg on installation flash USB.

The question - how could I possibly get the same behaviour as with installation disk so that it is recognized 'at once'?

Thanks for ideas if any.
Ivars

---

### Post by ivarss on 2011-05-09
Taking liberty to answer my own question :/

Obviously, the difference between Installation flash USB and external USB with Ubuntu installed is that the later did not have efi/boot directory on msdos (FAT) formatted partition.
If such partition and directories are present then Apple firmware recognizes the external disk as possible boot choice.

the abovementioned efi/boot directory must contain bootx86.efi file (for 64-bit EFI systems like mine) and grub.cfg with appropriate configuration.
bootx86.efi can be downloaded from internets or compiled yourself.

this information is scattered elsewhere but can be easily found even in these forums given that one knows exactly what to look for :)

This post helped me a lot:
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

cheers!
Ivars

---

### Post by pindar on 2011-05-09
May I take the liberty to ask how you managed to boot natty from a usb key? I've been successful with maverick, but never with natty. I do have a usb key with the magic EFI/BOOT partition and the appropriate ia386.efi, so I'd be grateful to know a bit more.

---

### Post by ivarss on 2011-05-09
Well, I didn't do anything special at all. Just created bootable USB flash disk from Natty Desktop 64-bit ISO image. With Startup Disk Creator application running on Ubuntu Maverick.
But as I am writing this, one thing comes to my mind, even if I do not know if that really matters.
I have 16 Gb USB flash with MBR partition table and TWO partitions.
First one is big and formatted for whatever is required for the moment (HFS+ or NTFS).
Second one is 1.2 Gb, and is HIDDEN.
I put Natty installation on this partition. Remember that EFI partition also is typically hidden.

Why? This way I have bootable USB stick, but bootable partition is not shown when key is plugged into Windows or OS X box.

Hope this helps,
Ivars

---

