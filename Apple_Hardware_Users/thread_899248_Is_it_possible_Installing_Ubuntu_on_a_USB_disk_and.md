---
title: "Is it possible? Installing Ubuntu on a USB disk and booting it on an iBook G4"
date: 2008-08-24
forum: Apple Hardware Users
---

### Post by Starlight on 2008-08-24
Hi! I'm curious to try Ubuntu on my iBook G4, but I don't want to lose anything I already have installed on the disk. Is it possible to install the PowerPC version of Ubuntu on a USB disk instead of the internal hard drive, so that when I boot with the USB disk plugged in I can pick whether I want to boot MacOS X or Ubuntu, and when I boot without the USB disk I can simply boot Mac OS X like I do now? :)

---

### Post by Starlight on 2008-08-25
Just bumping... does anyone know what will happen if I install Ubuntu on my iBook G4 on an USB disk as my second operating system, and then boot the computer without the USB disk inserted? Will it boot MacOS normally then?

---

### Post by pxwpxw on 2008-08-25
> **Starlight said:**
> Just bumping... does anyone know what will happen if I install Ubuntu on my iBook G4 on an USB disk as my second operating system, and then boot the computer without the USB disk inserted? Will it boot MacOS normally then?

It should do. If not, you can get back to macosx using your macosx install dvd to reset the startup disk.
You may have a struggle to get the usb stick booting, try it.

---

### Post by hvc123 on 2008-08-26
if your machine can boot form a usb stick then yer no problem just follow the how to on building a live usb. however if you machine cant boot form usb you will need to use a boot disk that points back to your usb.

either way its possible

---

### Post by Starlight on 2008-08-26
Thanks for the replies. :) I think I'll try it... the only thing I'm worried about is that I'm not sure how the Mac bootloader works.

When you install Ubuntu on a PC, it installs the Grub bootloader, which stores configuration files on the Linux partition. I don't know what would happen if I tried to boot the computer without the Linux partition, but I don't think that Grub would be happy with all its configuration files missing. So, if the bootloader that gets installed on the Mac installs its configuration files on the Linux partition, what can happen if I boot the iBook without the USB stick inserted?

---

### Post by tiresia on 2008-08-26
> **Starlight said:**
> Thanks for the replies. :) I think I'll try it... the only thing I'm worried about is that I'm not sure how the Mac bootloader works.

You may find interesting to read this link about Yaboot, the PowerPc Bootloader.
[http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/index.en.shtml](http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/index.en.shtml)

---

### Post by Starlight on 2008-08-31
Thanks :) I don't think I'll install Ubuntu on my iBook, though... I tried booting a Live CD and it ate my whole, fully charged battery in about 3 minutes. That was rather weird...

---

### Post by oswaldkelso on 2008-08-31
[PPC] How to make a Live CD a Live USB stick

[http://ubuntuforums.org/showthread.php?t=780320](http://ubuntuforums.org/showthread.php?t=780320)

---

### Post by hananias on 2008-08-31
I don't think ibooks PPC can boot from USB device...I've tried, and I read that the ibook g4 aren't design for that.  Only can they boot from a firewire ext drive.  I've done that and got it to work!
So inside the ibook g4 I had tiger, and on the outside i had ubuntu!:)

if someone else have a nice thread that argues that, or a "how to boot from usb in ibook g4" please let me know, because i'll like to try that:lolflag:

---

