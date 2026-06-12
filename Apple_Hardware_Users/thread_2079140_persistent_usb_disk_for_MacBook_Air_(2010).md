---
title: "persistent usb disk for MacBook Air (2010)"
date: 2012-11-01
forum: Apple Hardware Users
---

### Post by mfox on 2012-11-01
I was able to create a Ubuntu 12.10 installation disk on a usb stick that will boot my 2010 MacBook Air.  At the time I created it (with unetbootin), I made it persistent and included 5 gb storage.  The persistence works on a PC - if I boot it up and change the interface, and even add software, the changes show up on the PC.  But they don't on the Mac; even the added software doesn't show up as being installed.  This is true whether I boot up the usb on my MacBook Air or my iMac.

I suspect that the problem has something to do with the EFI folder that the Mac needs to be able to boot up, but I'm not sophisticated enough to know where to look or what configuration file or grub entry has to be modified to be seen when the Mac boots.  Speaking of grub entry, I did create one on the PC to allow persistence by copying the "try Ubuntu" grub entry and modifying it by adding the word "persistence" in the appropriate place.  I titled the entry "Ubuntu 12.10 Persistence", and the entry shows up when booting from a PC, but not from the Mac.  This is why I think that something in the EFI folder is pointing me to a different grub boot file.  Can anyone help me with this?

---

### Post by gizzardgulpe on 2012-11-02
I'm having a similar problem, only on *all* computers. 12.10 just doesn't seem to like saving settings on a live USB drive. I'm also using 12.10 64-bit, so I guess I'll try the 32-bit and see if the bug is there too.

---

