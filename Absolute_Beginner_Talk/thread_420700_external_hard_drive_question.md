---
title: "external hard drive question"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by whoarethey on 2007-04-23
I installed ubuntu last night and it ended up on my external hard drive. I really have no idea what I'm doing - I just thought I'd try it out. But now when I restart my laptop or turn it off, the external drive has to be hooked up to get the menu to choose between xp and ubuntu. Is there something I'm missing or a setting I need to change? Sorry if this seems vague..

---

### Post by ghansel on 2007-04-23
What happened is that the piece of software, called the bootloader, was installed on the external drive. Without the bootloader, called GRUB, an operating system cannot be loaded. To reinstall a bootloader on your internal hard drive, I suggest the following instructions.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good luck,
George

---

### Post by confused57 on 2007-04-23
> **whoarethey said:**
> I installed ubuntu last night and it ended up on my external hard drive. I really have no idea what I'm doing - I just thought I'd try it out. But now when I restart my laptop or turn it off, the external drive has to be hooked up to get the menu to choose between xp and ubuntu. Is there something I'm missing or a setting I need to change? Sorry if this seems vague..

Here's someone who experienced the same problem:
[http://ubuntuforums.org/showthread.php?t=420137](http://ubuntuforums.org/showthread.php?t=420137)

You might want to first install grub to the external hd mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
this will work, if your bios is capable of booting first to your USB external drive...if not, you can always use the Super Grub Disk to boot your external drive.

If you can boot first to your external drive and get a grub menu after installing grub to the mbr using the live cd, highlight your Ubuntu entry, press "e", then change root from (hd1,x)  to (hd0,x), then press "b" to boot...this change is temporary, but can be made permanent in your /boot/grub/menu.lst.

---

