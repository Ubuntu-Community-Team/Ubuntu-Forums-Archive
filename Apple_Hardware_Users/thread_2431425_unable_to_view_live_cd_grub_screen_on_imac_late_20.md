---
title: "unable to view live cd grub screen on imac late 2009"
date: 2019-11-16
forum: Apple Hardware Users
---

### Post by millerthegorilla on 2019-11-16
Hi, I have tried to use the ubuntu-studio live usb to overwrite my install of ubuntu-studio on an imac 2009.  If I set up the usb drive as mbr/fat I can see the pendrive listed under refind or under the mac device start up screen, but when I choose the grubx64.efi, I get a black screen.  If I use gnome-disk-utility to create a gpt partition scheme, with a fat partition, then my mac doesn't see the drive either in refind or in the device start up screen.

I normally have to add 'nomodeset' to the grub line, in order to see ubuntu when booting, but in this case it seems like grub has been compiled with the appropriated drivers for my machine.
I am currently waiting for balena etcher to copy the usb iso over, having created the usb drive geometry with mac disk utility.  I hope it works, but either way, I'll report back here, on what happens.

If it fails, I will try the standard ubuntu install for 19.10, to see if I can get to the grub screen on that.  If I can, then I guess it is probably a ubuntu-studio specific issue, and grub has been compiled without support for my machine (although I find that unlikely).

Ok.  I have just used Mac Osx Disk utility to create a disk as detailed here... [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0) and installed ubuntu-studio on the usb pendrive with balena etcher and it works.

Hurrah!

I'll place this here, just in case anyone else has issues with an older mac.

Thanks.

---

### Post by jeremy31 on 2019-11-16
Moved to Apple Hardware

---

