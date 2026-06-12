---
title: "Help Removing Need for USB Key"
date: 2012-08-10
forum: Any Other OS
---

### Post by PugnaciousPhlebotomist on 2012-08-10
I installed Linux Mint 13 KDE recently to try it out (although this is probably irrelevant to the problem) by creating a bootable flash drive, and it installed fine. However, now it requires a USB key on startup (the flash drive I used to install it to the system from). I do not remember checking a box in Ubiquity for this (or if there even is one), or going out of my to make this happen.

Is there a way to remove the need for a USB key to startup, or do I have to reinstall the distro?

To explain what happens now, if I turn the computer on without the key inserted, I have the option to load the BIOS before it automatically goes to a black screen with a blinking _ (underscore), where none of the keyboard buttons seem to have any effect.
When I do it WITH the flash drive in, it boots normally (I have it set to let me choose what device to boot from), but I want it so I can choose what OS to boot from without having the key inserted.

Sorry if there is a similar thread, but I couldn't find one. Thanks in advance for the help.

---

### Post by uRock on 2012-08-10
Not an ubuntu support request. Moved to ***Other OS/Distro Talk***

---

### Post by C.S.Cameron on 2012-08-10
I agree, mint is based on Ubuntu, the solution is common to both systems.

When you get to partitioning make sure your bootloader is installed on sda, not the flash drive.

Edit:
You should be able to fix the problem by removing the flash drive, once booted, and do an update-grub.

---

### Post by PugnaciousPhlebotomist on 2012-08-10
> **C.S.Cameron said:**
> I agree, mint is based on Ubuntu, the solution is common to both systems. 
Thank you. I got a warning for saying that I believed it was irrelevant.

> **C.S.Cameron said:**
> When you get to partitioning make sure your bootloader is installed on sda, not the flash drive.

Edit:
You should be able to fix the problem by removing the flash drive, once booted, and do an update-grub.
That worked, thanks for your help. Glad I could find someone who would give a useful response to my thread, I cannot tell you how much I appreciate that.

---

