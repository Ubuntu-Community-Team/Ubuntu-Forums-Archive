---
title: "[SOLVED] Boot from Usb hard drive using CD?"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by xzin on 2008-02-14
because my bios doesn't support directly booting from USB hard drive, I found a guide how to solve this. It was something about creating a boot CD which would then allow me to select the usb hard drive and start linux installed on it. But I can't find the guide now, so I would appreciate if you could help :)

---

### Post by dstew on 2008-02-14
If you have a Linux system installed on your USB hard drive, you can boot it using the [supergrub disk]("http://supergrub.forjamari.linex.org/"). You can even boot it with a [grub floppy]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy") if you have a floppy drive. If grub doesn't work (because you need some USB support software to access the USB drive, other than BIOS) you can use an Ubuntu Live CD. You can also make a [small Linux floppy]("http://www.linuxlinks.com/Distributions/Floppy/") that might work. I think the bootE linux fits on a single floppy. I don't know if it has USB support.

EDIT: [Pendrive linux]("http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/") is a USB distribution that provides a boot floppy. The commands for booting from the floppy look a lot like grub!

---

### Post by xzin on 2008-02-16
Thank you, I installed Super Grub Disk on CD and with that I was able to boot my Ubuntu from the USB hard drive. Everything is working great now :popcorn:

---

