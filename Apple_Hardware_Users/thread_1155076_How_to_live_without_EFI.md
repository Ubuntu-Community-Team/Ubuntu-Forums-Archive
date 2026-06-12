---
title: "How to live without EFI"
date: 2009-05-10
forum: Apple Hardware Users
---

### Post by blippy on 2009-05-10
It's complicated ....

I seem to have fritzed my EFI partition some time in the past. I currently have Ubuntu installed in one partition, and Windows 7 in another. I installed Win 7 this morning. I don't think it is the root of my problem, because since installing Jaunty, whenever I booted, I got a white screen for maybe 30 seconds before grub started.

Jaunty is in /dev/sda1.

I inserted my Leopard disk, but I couldn't install to a spare partition (there is currently no OS X on my system). It complained that the HD needed to be zapped so that a GUID table could be created. I don't want anything zapped at the moment, because I'm actually happy with my partition layout. I inadvertently told my iMac to reboot from the network. The only options that the Leopard disk gives me is to boot from the DVD, or the network; not the HD.

When I reboot my machine, I now get the network boot logo, and nothing else. In order to boot to an operating system, I have GAG (a primitive graphical bootloader) on CD, so I boot my computer whilst holding the C key to bring up the GAG loader. From there, I can boot either Jaunty or Windows 7.

This is rather time-consuming and inconvenient, as I'd rather have grub come up, or even GAG come up - I DO want it installed in my MBR, though, rather than have to fiddle with CDs. I would rather not have EFI, because I don't have OS X installed (nor will it let me install it without repartitioning the drive), there's probably no space on the drive to house an EFI partition (Jaunty is in sda1), and besides, I don't especially want it.

Any suggestions on how I can persuade my iMac to just boot from the MBR, and drop the whole EFI thing?

BTW, Windows 7 - it's not turning out all that bad, actually. But maybe that's for another thread. :tongue:

---

### Post by cyberdork33 on 2009-05-12
Please check the FAQ. There is a thread about blessing.

---

