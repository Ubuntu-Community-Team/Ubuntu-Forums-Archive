---
title: "How do I access BIOS on Lombard?"
date: 2010-05-25
forum: Apple Hardware Users
---

### Post by khelben1979 on 2010-05-25
I want help with accessing the BIOS on a Powerbook G3 Lombard (1999). Anyone?

---

### Post by linuxopjemac on 2010-05-25
There is no BIOS in a Lombard. You can access the Open Firmware by holding option+command+o+f when you boot:

[http://mac.linux.be/content/openfirmware](http://mac.linux.be/content/openfirmware)
[http://mac.linux.be/content/guide-open-firmware-apple-bios-0](http://mac.linux.be/content/guide-open-firmware-apple-bios-0)

---

### Post by khelben1979 on 2010-05-25
> **linuxopjemac said:**
> There is no BIOS in a Lombard. You can access the Open Firmware by holding option+command+o+f when you boot:

[http://mac.linux.be/content/openfirmware](http://mac.linux.be/content/openfirmware)
[http://mac.linux.be/content/guide-open-firmware-apple-bios-0](http://mac.linux.be/content/guide-open-firmware-apple-bios-0)

I press the keys:  fn + alt + o + f  but nothing happens. Hmm..?

---

### Post by linuxopjemac on 2010-05-25
not fn

The alt+apple+o+f after the boot boing

---

### Post by linuxopjemac on 2010-05-25
also nice:
[http://mac.linux.be/content/booting-open-firmware](http://mac.linux.be/content/booting-open-firmware)

---

### Post by khelben1979 on 2010-05-25
If you have a complete list of commands which can be used from open firmware, it would be of great importance in what I'm trying to do: booting Linux from an USB stick.

---

### Post by linuxopjemac on 2010-05-25
Don't look further, have a look at my Linux Mint installation instructions:

[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)
[http://mac.linux.be/phpBB3/viewtopic.php?f=10&t=91&p=125#p125](http://mac.linux.be/phpBB3/viewtopic.php?f=10&t=91&p=125#p125)

---

### Post by khelben1979 on 2010-05-25
Okay. On my system over here it didn't like that I tried to install Debian Squeeze on my USB stick. I got some errors.

I will look further for a iso image which accepts an usb stick as installation media. I got stuck at the present... All the partitions will get mounted on the usb stick and it seems like I need to get into Open Firmware mode everytime before Linux boots up if not the Yaboot bootloader can accept the usb stick, that remains to be seen if it's possible on this old Powerbook.

Thanks for your help so far and because of the title of this thread, I should mark it as solved! :)

---

### Post by 3rdalbum on 2010-05-25
As far as I know, you can't boot from USB devices on that era of Mac. Only Firewire, if your machine has it.

---

### Post by linuxopjemac on 2010-05-25
3rdalbum, not true. I did it many times.

---

### Post by linuxopjemac on 2010-05-25
I did the mini.iso of Debian Lenny, as in the installation instructions I give you for installing Linux Mint LXDE Debian PPC.

[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)

---

### Post by 3rdalbum on 2010-05-25
> **linuxopjemac said:**
> 3rdalbum, not true. I did it many times.

Ahh, okay then. I was always under the impression that Apple didn't allow it on their hardware, but maybe that's just for booting Mac OS.

---

### Post by sha.goyjo on 2010-05-25
> **linuxopjemac said:**
> 3rdalbum, not true. I did it many times.

You've booted from USB on a Lombard? This tutorial doesn't boot from USB, it boots from CD and then uses a USB. That is functionally different from "booting from usb", which the lombard can't do. I think that's the cause of the confusion.

---

### Post by linuxopjemac on 2010-05-25
Sha.Goyjo: if you read carefully you would understand that the manual is for installing from USB or CD not USB and CD. I am the one who wrote that manual, I should know it. I installed Linux Mint LXDE PPC via USB, so I am 100% confident that it works.

---

### Post by sha.goyjo on 2010-05-25
> **linuxopjemac said:**
> Sha.Goyjo: if you read carefully you would understand that the manual is for installing from USB or CD not USB and CD. I am the one who wrote that manual, I should know it. I installed Linux Mint LXDE PPC via USB, so I am 100% confident that it works.

Okay, I see what you are saying here, but I've tried it on all of ppc macs (see below) with no success. Maybe Khelben will have more luck.

Also, if you have any grievances about the way I post (or would like to argue with me about my ability to read :) ) please feel free to pm me. I don't like to wast space on troubleshooting threads.

---

### Post by khelben1979 on 2010-05-25
From what I have read, it seems that it would be possible to boot Linux from the usb stick as linuxopjemac has written in the manual. If it works, it would mean that either Yaboot takes care of that, or that I would need to add a command line from inside the open firmware prompt.

I will probably see the result later tonight if it works or not (swedish time) or tomorrow since it takes a very long time to load/write from the usb stick since it uses USB 1.1. :)

---

