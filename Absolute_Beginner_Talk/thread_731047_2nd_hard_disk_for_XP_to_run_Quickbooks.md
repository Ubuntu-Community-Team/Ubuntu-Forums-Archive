---
title: "2nd hard disk for XP to run Quickbooks"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by iainv on 2008-03-21
I'm running 7.10 off a hard disk, but need to run Quickbooks and a scanner that won't work on Ubuntu.

I've got a small (8GB) slave drive (/dev/hdb) mounted as /mount/disk but basically I want to install a copy of XP on this, to just run Quickbooks and use the scanner.

Is there a way to install XP on only this disk, boot normally into Ubuntu but have a "Shut down and restart in Windows" option?

I don't want a dual-boot screen every time I turn the machine on as i'm trying to stick to Ubuntu.

The other option would be Virtual Box, but I can't seem to get this to write only to the small disk, and it wouldn't work with my scanner anyway!

Help please!

Iain

---

### Post by brandonclyon on 2008-03-21
I dont know about the scanner but you could try loading Quickbooks through Wine and see if that gives you the functionality that you are looking for.

---

### Post by iainv on 2008-03-21
WINE doesn't appear to work well for Quickbooks at all (according to winehq and google), and won't solve my scanner issues, so unfortunately I don't think it's an option.

Iain

---

### Post by brandonclyon on 2008-03-21
Hmmm well I dont think you will be able to get around the boot loader like Grub, but really its not that severe, it only adds maybe 8 seconds to your boot time if you just let it sit there and it will give you the option to run XP to run quickbooks/scanner stoof.

---

