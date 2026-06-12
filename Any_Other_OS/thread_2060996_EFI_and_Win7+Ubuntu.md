---
title: "EFI and Win7+Ubuntu"
date: 2012-09-21
forum: Any Other OS
---

### Post by HrKristian on 2012-09-21
I've done something stupid.

When I first installed Ubuntu, things went mostly fine, the machine had Windows 7 installed already and I wanted to add Ubuntu.
EFI made a bit of a mess of things, long story short I booted into a live session and used boot-repair to fix GRUB for me.

This made GRUB list 4 Windows boot alternatives and the usual two Ubuntu options.

Then I did something stupid. I managed to format the EFI partition.
A live session boot-repair fixed the issue of booting Ubuntu, but, I can't boot Windows anymore.
The GRUB menu has the usual Linux entries, and one Windows entry, which is the entry you get on a regular (BIOS) boot.
When I select the Windows entry, I get a message about wrong EFI file path and stuff...
I'm assuming the other alternatives were boot images located on the EFI partition? Since there used to be a Windows folder there before.
Well, that's gone, obviously, and, Windows "repair" is compeltely unable to repair that, and I haven't found a single thread or site offering a solution to my problem, so I'm here.

Would it be enough to just replace the missing Win7 EFI files?
Alternatively is there another way to solve this?

---

### Post by oldfred on 2012-09-21
The files you need are the same one's grub is chain loading to (not grub2's os-prober, but the one's Boot-Repair creates). Depending on how it is mounted as this is mounted in /boot/efi:

/boot/efi
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi

I know with XP there were backups in this
C:\windows\ServicePackFiles\i386

You can look in your Windows 7 DVD or your Windows repairCD or USB. You did make a repairCD?

I think Boot-Repair backs up essential files, but they they are ususually in the same partition.

---

### Post by HrKristian on 2012-09-22
Thank you for the filenames, there were backups on the Windows partition.
However copying them over (into their correct subfolder) on the EFI drive and running boot-repair didn't help much, I got two additional entries in the GRUB menu, but choosing the windows "UEFI Boot Loader" gave me a Windows error about having to use windows repair and stuff, so, gonna fiddle around some more...

---

### Post by oldfred on 2012-09-22
Can you directly boot from UEFI/BIOS (not grub menu) and use f8. Do not know if f8 still works in UEFI version, but there should be a way to get to the repair console.

If you have access to another Windows7 install. Has to be either 32 or 64bit to be the same as yours.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

