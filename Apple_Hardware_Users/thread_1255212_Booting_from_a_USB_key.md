---
title: "Booting from a USB key"
date: 2009-09-01
forum: Apple Hardware Users
---

### Post by skmando on 2009-09-01
Hi,

I have a MacBook Pro 5,1 as a work machine. I've started using ubuntu on an old P4 laptop I have at home and love it, but want to experiment with it a bit more on a more powerful machine.

Unfortunately I can't really install a new or additional OS on the machine at the moment, but was wondering if it was possible to create an install of Ubuntu 9.04 to run direct from a USB key?

Rather than running in 'Live mode', is it possible to have it working so applications can be installed, graphic drivers set, documents created and edited - basically so the usb key is the harddrive? If it is possible, would the Ubuntu installation be able to read and write data on the internal harddrive? Ideally be able to use this, then reboot into OS X afterwards.

Very new to Linux so I apologise if I've just asked a question that has an obvious answer or has been answered a load of times in the forum.

I intend to backup and re-partition my computer at a later date to have a 'proper' installation of ubuntu on the machine, but now is not the best time to do so as I'm using my work machine flat out at the moment and haven't the time to do it.

Any advice would be gratefully received.

S.

---

### Post by karamu on 2009-09-01
I don't have direct experience of working in a live environment for an extended period but I am pretty sure if you install a live CD on a USB key it will save documents on it.

And yes, you can access the local HDDs from the live Ubuntu session.

I use a program called Unetbootin to make a bootable USB key- it works on Windows and Linux but not I think Mac:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Good luck!

---

### Post by automaton26 on 2009-09-01
I'm not sure if there's any Mac-specific issues, but normally you can just download the .iso file for ubuntu 9.04, and then:

1) Check the MD5SUM of the file, to be sure it is exactly correct.

[INDENT][https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")[/INDENT]

2) Use the "USB Creator" application to create a LiveUSB from it.

[INDENT][http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator")[/INDENT]

---

### Post by C.S.Cameron on 2009-09-01
Most new computers see a USB key as just another hard drive so you can just plug it in and run install from the live CD. I would suggest disabling the internal hard drive first to avoid installing grub on it, (as the computer will no longer start without the key if this happens).
Running off a bargain flash drive can be considerably slower than running off a SATA hard drive.
You can also install to your USB key using usb-creator which can make a persistent disk image install of the Live CD. This is more compact than the above method but is not as upgradeable.

---

### Post by amd-64 on 2009-09-01
Has anyone tried booting off the SSD in a macbookpro (mid 2009).  Would it be slower than a usb.

---

