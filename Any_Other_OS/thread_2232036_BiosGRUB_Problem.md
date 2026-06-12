---
title: "Bios/GRUB Problem"
date: 2014-06-29
forum: Any Other OS
---

### Post by Jim_Walters on 2014-06-29
I have Ubuntu 14.04 i386 installed on an old Sony Vaio desktop (PCV-RS620g). Don't know what specifically happened but, when system boots it seems to read fine for first half then hiccoughs and remaining boot process becomes erratic. Funny thisng is it eventually boots to desktop screen. Here's the problem...I have no control with either mouse or desktop. I've tried all types of rescues. It will not boot from disk, flash drive.  Apparently, during the erratic segment of BIOS it is not seeing the drivers for keyboard/mouse.
Any suggestions would be greatly appreciated!

---

### Post by Bashing-om on 2014-06-29
Jim_Walters; Well,

A thought, Bios has reset .. How bout going back into bios and resetting bios to the default values, and if still problems with the mouse and keyboard change the settings for "usb devices" the plug and play options.

See if that has any effect.
After all it is a process, and it all starts
[INDENT][INDENT][INDENT][INDENT]in bios
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by slonk on 2014-06-30
Are you using a USB keyboard and/or are you using a USB hub? You might have to use a PS/2 adapter to go into the BIOS and turn on legacy support for the input devices.

Also, please don't say "hickups" without giving more specific error messages.

---

### Post by buzzingrobot on 2014-07-01
Devices can often be enabled or disabled -- in effect, made invisible to the OS -- in the BIOS, but device drivers are in OS territory. In Linux, drivers are usually in the kernel.

The BIOS passes control to the bootloader, in this case, Grub. So, if the machine boots to to a normal "desktop screen", the BIOS and Grub are very likely doing what they are supposed to do.

---

