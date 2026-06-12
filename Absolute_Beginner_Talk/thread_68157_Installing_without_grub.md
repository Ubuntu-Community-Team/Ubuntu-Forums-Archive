---
title: "Installing without grub?"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by pawnUz on 2005-09-22
Hi

I was wondering if there is a way to install grub AFTER the installation of Ubunto is complete so if the installation screws up i'm not stuck with GRUB error on bootup. I want grub only if the installation was successfull.

Also how do i boot ubunto (on a successfull install) without grub (before i install it)?

Is there a way to do this and how?

Thanks

---

### Post by matthewv on 2005-09-22
How about just running through the default install until the installer asks you to install GRUB. Select No and it will present you with a list of places to install it. If you install it to a floppy disk then you can get to the GRUB boot options by booting off the floppy disk. Booting without the floppy will start your existing operating system.

If Ubuntu works you can install GRUB to your hard drive with the command "grub-install /dev/hda" to install to your MBR.

I've installed Ubuntu on my system by putting GRUB on floppy but I still use the floppy as I don't want to risk problems.. but I think the risk is extremely low... I've never had problems with GRUB.

---

### Post by pawnUz on 2005-09-25
[QUOTE=matthewv]How about just running through the default install until the installer asks you to install GRUB. Select No and it will present you with a list of places to install it. If you install it to a floppy disk then you can get to the GRUB boot options by booting off the floppy disk. Booting without the floppy will start your existing operating system.

If Ubuntu works you can install GRUB to your hard drive with the command "grub-install /dev/hda" to install to your MBR.

I've installed Ubuntu on my system by putting GRUB on floppy but I still use the floppy as I don't want to risk problems.. but I think the risk is extremely low... I've never had problems with GRUB.[/QUOTE]

I was gonna try what you said today when it suddenly hit me, my laptop doesnt have a floppy... Can you install GRUB on an USB memory stick or something?

The reason i don't want to install GRUB is because i've had trouble installing ubunto on laptops before. Something goes wrong with the install and i cant boot ubunto and the only way to remove it is to delete the partitions which messes up GRUB and then i cant boot windows.

So, if memory stick wont work, is there any other way?

---

### Post by matthewv on 2005-09-26
The memory stick would be great, but I don't know if that would be possible from within the Ubuntu installer. You could always install Ubunutu without GRUB and use rescue mode to boot into it, but I would probably install GRUB to your root partition, or, if you made one, your /boot partition. You could then use another boot loader, e.g modifying your windows boot.ini to boot to that partition. I've never tried anything with the boot.ini, but I don't see why that shouldn't work.

---

### Post by pawnUz on 2005-09-27
[QUOTE=matthewv]The memory stick would be great, but I don't know if that would be possible from within the Ubuntu installer. You could always install Ubunutu without GRUB and use rescue mode to boot into it, but I would probably install GRUB to your root partition, or, if you made one, your /boot partition. You could then use another boot loader, e.g modifying your windows boot.ini to boot to that partition. I've never tried anything with the boot.ini, but I don't see why that shouldn't work.[/QUOTE]

So what you mean is that i create an empty partition as usual and choose to install GRUB on it, then modify the windows boot.ini to have that partition as an boot option? If thats the case, i have no idea how to add a boot option to boot.ini (what to write).

Aren't there any free/shareware boot programs that are easy to configure (i.e adding boot options).?

---

### Post by matthewv on 2005-09-27
Here's how I think you do it:
Install Ubuntu and then install grub to your Ubuntu root partition (or /boot if you have one). Then, restart your computer and windows should boot. Once in windows, right click on My Computer, select Properties, go to the Advanced tab, and press settings under Startup and Recovery. Press Edit to edit your boot.ini. Add a new line that reads:
multi(0)disk(0)rdisk(0)partition([number of partition you installed grub to])="Ubuntu Linux"

That should work. I've never done it, but I think that's how its done. If its not, maybe someone will correct me.??

---

### Post by Scuddie on 2005-09-27
That does not work.  I have tried that more than once in the past, but to no avail.  If that worked, people wouldn't need LILO ;).

I dont know if it has to do with the fact that MS is "incompatible" with anything other than FAT and NTFS, or maybe linux requires a bootloader?  I'm not sure which it is, but probably the former.

---

### Post by matthewv on 2005-09-27
but if you install the grub bootloader to the ubuntu root partition, shouldn't ntldr (ms bootloader) pass boot control to that partition... same as making the partition bootable with a tool like fdisk??

---

