---
title: "Install to USB HD, boot from CD"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by carolus on 2008-02-22
On a Windows XP or Vista computer, is there some reasonably easy way to install Ubuntu to an external USB hard drive, then boot it from a CD (either the Ubuntu Live disk or some other kind of boot disk)?  I would like to avoid monkeying with the Windows installation or the BIOS configuration, especially when the computer is not my own.  USB hard drives are now cheap, small, and portable.

---

### Post by marufaberlin on 2008-02-22
Yeah... of course you can. Just install onto the external hd, put grub there, and put the external hd in front of the normal HD in the BIOS boot order. Ubuntu even runs from pen drives. If you google it, you'll find a lot of tutorials.

---

### Post by ATAQ on 2008-02-22
Sure why bother installing it at all if you dont wanna use it as a primary system, Just use the Live CD sessions.

---

### Post by marufaberlin on 2008-02-22
Running from a live CD has a few disadvantages:

You can't read or write other CDs if you don't have enough RAM
You can't install additional programs,
You can't save your files as easily

There are ways past these problems, but seeing as you need some kind of external hd for all of them, it would be easier just to install to one.

---

### Post by marufaberlin on 2008-02-22
Oh... i forgot, the most annoying thing is that live CDs are **slow**

---

### Post by carolus on 2008-02-22
> **marufaberlin said:**
> Yeah... of course you can. Just install onto the external hd, put grub there, and put the external hd in front of the normal HD in the BIOS boot order. Ubuntu even runs from pen drives. If you google it, you'll find a lot of tutorials.

As I said, I don't want to monkey with the BIOS, especially on someone else's computer.  They vary enough from one manufacturer to another that this can be troublesome on an unfamiliar machine.

---

### Post by dstew on 2008-02-22
Once you install on a USB hard drive, you can boot it from a grub CD or floppy. See [supergrub disk.]("http://supergrub.forjamari.linex.org/")For a grub boot floppy, see [here]("https://help.ubuntu.com/community/GrubHowto/BootFloppy").

---

### Post by carolus on 2008-02-22
In the "howto's" for USB pen drives, the method advocated when the BIOS does not permit booting from USB, is to use a "boot floppy"  that passes control to the USB drive.  One can find such  boot floppies on the web, but newer machines don't have floppy drives,  I can't find the counterpart in a CD, but it seems there should be no difference in principle.  Maybe one only has to convert the boot floppy to an .iso file and burn it to a CD, but I'll leave that to someone who understands how it works. 

 I would rather boot from a disk than have to alter and  restore the BIOS, even when the BIOS permits the change.  I'm both lazy and risk-averse.

---

### Post by dstew on 2008-02-22
Use the supergrub disk. It comes as an .iso Burn it and you get a very capable grub-based booter.

---

### Post by carolus on 2008-02-22
Thanks dstew, it looks like Super Grub Disk will handle the problem of booting from a CD.  The  screenshots show an option "Boot GNU/Linux" that is supposed to find  an existing grub menu and allow you to select and boot. I presume this will find grub on a USB hard drive. 

Then as manufaberlin advised, "install onto the external hd, put grub there".   Is it obvious how to do this from the Ubuntu installation options, or is this configuration sufficiently  nonstandard that you have to know some tricks?

---

### Post by dstew on 2008-02-22
> I presume this will find grub on a USB hard drive. It should find it.> Then as manufaberlin advised, "install onto the external hd, put grub there". Is it obvious how to do this from the Ubuntu installation optionsIt might not be obvious. The installer usually installs grub onto the boot hard disk by default. When you get to the very end of the installation, be careful. You have to know the grub-name of the external drive to get it right. If you have only one internal hard drive, and one external drive, my guess is that your external drive will have the name (hd1) because grub counts from zero.

Another option (which I might do, being a fan of grub) is to not install grub at all. Even then, you might be able to boot using the supergrub disk. You can even install grub from the supergrub disk if you need to. It is not too hard to do, and you can use the grub command line to make sure you are installing to the correct place.

---

### Post by marufaberlin on 2008-02-25
Well, even if you boot from a CD or Floppy, these must be above the hard drives in the BIOS boot order.

---

### Post by carolus on 2008-02-25
> **marufaberlin said:**
> Well, even if you boot from a CD or Floppy, these must be above the hard drives in the BIOS boot order.

I haven't encountered a PC that did not allow you to boot from either a floppy or a CD,  but neither of my two computers offers an option to boot from  USB.  On my newer computer, a low-end Sony laptop about 2 years old, the BIOS boot options are HDD, CD, and floppy - despite the fact that it is sold with no floppy drive, and no place for an internal one.

It sounds like booting from the Super Grub Disk, then referencing GRUB on the USB,  can solve this problem.

---

### Post by marufaberlin on 2008-02-28
My machine (an ASUS M2V) mainboard recognizes even USB sticks, and lists them as hard drives. Some people disable CD booting, out of security reasons.

---

### Post by stalkingwolf on 2008-02-28
Many systems offer a choice to open boot menu.  A keystroke or combination of them will open the
menu.  It might be F2, F12, or a combination like esc +del..  This option is a one time thing and doesnt
change the boot order in the BIOS.

---

