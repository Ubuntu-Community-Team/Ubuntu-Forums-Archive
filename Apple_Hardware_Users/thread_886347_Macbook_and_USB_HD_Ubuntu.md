---
title: "Macbook and USB HD Ubuntu"
date: 2008-08-11
forum: Apple Hardware Users
---

### Post by WeeManFoo on 2008-08-11
I want to use my external USB hard drive to run Ubuntu on my new Macbook.  I have been to pendrivelinux.com and found how to install Ubuntu on an external drive but I can't get it to boot on my Mac.  I don't want to use boot camp or touch in any way the partitions on my Mac.  Is there any way to make this work?  Also, if I install Ubuntu on a USB flash drive, can I make that boot from my Mac?

---

### Post by Kobalt on 2008-08-11
You can do that, just make sure to install Grub on the MBR of your external HDD.
At boot time of your Mac you can select from which medium you can boot by pressing the option key. Select you external HDD, and here you go...

---

### Post by cyberdork33 on 2008-08-11
> **Kobalt said:**
> You can do that, just make sure to install Grub on the MBR of your external HDD.
At boot time of your Mac you can select from which medium you can boot by pressing the option key. Select you external HDD, and here you go...
Have you tried this on a Mac? Booting from an external device does not work for most. There is an extensive thread of findings linked in the FAQ.

---

### Post by nurseman on 2008-10-28
Hold down the options key when you mac boots up. This should give you your drives to select.

---

### Post by ronocdh on 2008-10-29
> **nurseman said:**
> Hold down the options key when you mac boots up. This should give you your drives to select.
I think cyberdork's right... really, booting from an external on a Mac is more trouble than it's worth, IMO. FireWire might be a little easier, but if you're going to format an external drive with an MBR and then on top of that set up GRUB there, then install Ubuntu... ugh, just install on the internal already!

The GParted live CD can resize partitions pretty well. You can even resize your OSX partition from within OSX! (Or you can reinstall everything, if that floats your boat.)

Do check the FAQ. Hopefully it will discourage you from pursuing this external drive thing, and maybe prevent a lot of hair-pulling, too.

---

### Post by WaeV on 2008-10-29
The way I understand it, the mac bootloader can boot to "legacy OSes", but only if they are on the main HD.  Installing GRUB to the main HD would solve your problem.

---

