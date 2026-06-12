---
title: "Is it even possible to install Ubuntu 16.04.4 onto a Macmini1,1?"
date: 2018-07-08
forum: Apple Hardware Users
---

### Post by dalekky on 2018-07-08
I am trying to install Ubuntu 16.04.4 desktop 32-bit OS onto a 2006 Apple Mac Mini (model macmini1,1)

So far nothing I've tried has worked.

1. Tried booting the Mac straight from an unaltered burned Ubuntu install DVD
result = fails to boot with "Failed to load ldlinux.c32" error.

2. Tried the official tutorial for installing Ubuntu onto a Mac here: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0)
result = impossible to install Etcher software on a 2006 Apple Mac Mini (OS 10.5.8)

3. Tried making a bootable USB drive using Unetbootin from here: [https://unetbootin.github.io/](https://unetbootin.github.io/)
result = impossible for Unetbootin to recognize ANY USB drive plugged into the Mac, even when it is formatted as FAT32 by either the Mac itself or another computer.

4. Tried using dd in terminal
result = not recognized by the Mac on boot up

5. Tried using xorriso method explained here: [http://coderazzi.net/linux/macmini2006/macmini.htm](http://coderazzi.net/linux/macmini2006/macmini.htm)
result = the created ISO fails to boot with a "Failed to load ldlinux.c32" error message

6. what can I try next????

---

### Post by jeremy31 on 2018-07-08
Moved to Apple Hardware

---

### Post by dalekky on 2018-07-08
attempt 6. Tried using the method described here (the answer that talks about converting the ISO to a DMG and using dd to copy it to the USB) [https://askubuntu.com/questions/28495/how-do-i-get-my-mac-to-boot-from-an-ubuntu-usb-key](https://askubuntu.com/questions/28495/how-do-i-get-my-mac-to-boot-from-an-ubuntu-usb-key)
result: USB drive does not show up as a bootable drive when the Mac is restarted.

---

### Post by dalekky on 2018-07-09
I have a question... if I upgrade the 32-bit CPU (currently Intel Core Solo) to a 64-bit Intel Core 2 Duo processor, and install the highest Mac OS this hardware can run (10.6 Snow Leopard), would that also upgrade the mac's boot manager and make it easier to install Ubuntu?

---

### Post by kevin160 on 2018-07-12
I could be wrong, but I don't think you can install from a USB stick on that model.  Installing anything on my 1st gen mac pro requires either using the internal CD/DVD or an external *firewire* CD/DVD drive.  

debian still makes ISOs for 32 bit processors and 32 bit efi.  Grab the "unofficial" version that has firmware on the disk:  

[https://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/9.4.0+nonfree/i386/](https://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/9.4.0+nonfree/i386/)

If that doesn't work for you, the simplest solution will probably be putting your mini into "Boot Camp" mode and using the Ubuntu 16.04 32-bit (BIOS mode) ISO.  This may or may not leave you unable to use some of the mini's hardware.  

Worst case, you can pull the drive out of it and put it into another computer or a USB enclosure, install 32-bit ubuntu on that, manually install grub-efi-ia32, and then move the drive back into your mini.  I've had success in the past using debootstrap for this.  It is time consuming and very fiddly though.  

Honestly, I'm not sure it's worth the trouble of upgrading the processor.  Sure, it will be faster, but hardware that old is basically going to die any day, especially if you start mucking with the motherboard, etc.  Unless you are looking for a technical challenge, get something that has a proper 64-bit EFI and you'll be much happier.  How much RAM do you have, by the way?  Anything less than 2 GB is not going to run a 64-bit OS very well.

---

### Post by dalekky on 2018-08-17
I installed the new cpu. The mini has 2Gb ram.

I found the only way to get it the i386 16.04 installer DVD to boot on the mac mini was to first install Mac OS 10.6 snow leopard (which must have updated something, possibly firmware), then the 32bit Ubuntu 16.04 disk booted and installed fine after that.
I did also try to make it install the 64bit 18.04 OS, but this was impossible since it couldn't boot the 64bit installer.

so.. thread solved with solution = install Mac OS 10.6, update, reboot and install from ubuntu-16.04.4-desktop-i386 dvd

---

