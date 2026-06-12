---
title: "Grub2 Can't Find Kernel"
date: 2016-11-08
forum: Any Other OS
---

### Post by Trevor_Owen on 2016-11-08
For several years now I have successfully triple-booted my computer with Lubuntu, Windows 7 (now 10), and various versions of Android x86.  Last Saturday I installed the Clockworkmod 13 version of Android x86, modified the 40-custom file in /etc/grub.d as I have in the past, and was successfully able to boot CM13 using the Grub menu.  Unfortunately I neglected to use the CM13 settings to prevent CM13 from suspending, as I have found in the past when Android x86 suspends on my computer it breaks the boot record somehow, and I have had to use Boot Repair to get back into business.  When I discovered I was unable to boot I used a Boot Repair live cd to re-install Grub. After I booted into Lubuntu I wrote a wrote a new 40_custom file entry for CM13 identical to the original (cut and pasted back-up, actually), made the file executable, and ran update-grub.  I checked in Grub Customizer to make sure the CM13 entry appeared, then rebooted to get into CM13.  When I selected CM13 and pressed "Enter", I got the following error messages:

/cm-x86-13.0-rc1/kernel not found

You need to boot kernel first.

I have checked and re-checked the 40_custom until I am cross-eyed, and probably wouldn't see an error now if it jumped at me.  Android is installed in sda3 (Confirmed from GParted), the line set root='(hd0,3)' should point Grub to the correct partition, and the kernel is located in /cm-x86-13.0-rc1.

Maybe a fresh pair of eyes can find what I am so obviously missing.  Any help greatly appreciated.

Here is the CM13 entry in 40_custom

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Android-x86 2.2 (MDPI)" {
set root='(hd0,3)'
linux /cm-x86-13.0-r1/kernel quiet root=/dev/ram0 androidboot_hardware=generic_x86 acpi_sleep=s3_bios,s3_mode SRC=/cm-x86-13.0-r1 DATA= DPI=160
initrd /cm-x86-13.0-r1/initrd.img
}

menuentry "Android-x86 2.2 (HDPI)" {
set root='(hd0,3)'
linux /cm-x86-13.0-r1/kernel quiet root=/dev/ram0 androidboot_hardware=generic_x86 acpi_sleep=s3_bios,s3_mode SRC=/cm-x86-13.0-r1 DATA= DPI=240
initrd /cm-x86-13.0-r1/initrd.img
}

menuentry "Android-x86 2.2 (VESA)" {
set root='(hd0,3)'
linux /cm-x86-13.0-r1/kernel quiet root=/dev/ram0 androidboot_hardware=generic_x86 acpi_sleep=s3_bios,s3_mode SRC=/cm-x86-13.0-r1 DATA= vga=788
initrd /cm-x86-13.0-r1/initrd.img
}

menuentry "Android-x86 2.2 (Debug mode)" {
set root='(hd0,3)'
linux /cm-x86-13.0-r1/kernel root=/dev/ram0 androidboot_hardware=generic_x86 acpi_sleep=s3_bios,s3_mode DEBUG=1 vga=788 SRC=/cm-x86-13.0-r1 DATA=
initrd /cm-x86-13.0-r1/initrd.img
}

---

### Post by howefield on 2016-11-08
Moved to the "*Any Other OS*" forum.

---

