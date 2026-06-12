---
title: "rEFInd not seeing new installation on MacBook"
date: 2017-07-03
forum: Apple Hardware Users
---

### Post by Donnut on 2017-07-03
Hi all. I am trying to set up a triple boot system on my MacBook Pro, early 2015. I did a fresh install of OS X, partitioned my drive using Disk Utility, formatted them in Gparted, and installed Ubuntu. Now, rEFInd won't see/boot Ubuntu. Does anyone know what the problem could be?

---

### Post by Donnut on 2017-07-03
Oh, I did use ubiquity -b to avoid installing the grub boot loader. I was worried that would effect the EFI partition.

---

### Post by Donnut on 2017-07-03
So I've made some progress, if I use the USB image to boot rEFInd, it finds the Ubuntu installation, but the version installed in the EFI partition doesn't. Can someone please give me any advice on this?

---

### Post by &amp;KyT$0P# on 2017-07-04
> **Donnut said:**
> Oh, I did use ubiquity -b to avoid installing the grub boot loader. 
There's your problem.  I'm not sure it's possible to boot Ubuntu without GRUB.

Did you add the ext4 driver to rEFInd? - [http://www.rodsbooks.com/refind/drivers.html#installing]("http://www.rodsbooks.com/refind/drivers.html#installing")

---

### Post by Donnut on 2017-07-04
Thanks. I re-installed it with Grub, and while it overwrote rEFInd and booted straight into Ubuntu, all I had to do was use Option to get into OSX and re-install it. Works perfectly now.

---

### Post by &amp;KyT$0P# on 2017-07-05
You're welcome. :KS

> **Donnut said:**
> while it overwrote rEFInd and booted straight into Ubuntu, all I had to do was use Option to get into OSX and re-install it.
rEFInd probably wasn't overwritten.  GRUB puts itself first in the boot order.

You may also be able to fix that using [FONT=Courier New]efibootmgr[/FONT] from within Ubuntu.  Just set the boot order to put rEFInd first (run [FONT=Courier New]sudo efibootmgr -v[/FONT] to figure out what's what).

Refer to [FONT=Courier New]man efibootmgr[/FONT] for more info.


(I've successfully used [FONT=Courier New]efibootmgr[/FONT] on my MacBook Pro more than once, but I don't have a early 2015 MacBook Pro.  If you don't have prior experience with changing boot order from [FONT=Courier New]efibootmgr[/FONT], you might want to back up your system before trying it.)

---

