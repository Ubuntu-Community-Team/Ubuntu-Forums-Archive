---
title: "reinstalling ubuntu"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-08-14
I have a dual-boot system with Win XP and Ubuntu

Both are on separate HDD... However, ny ubuntu HDD being old, i fear that it is likely to crash in near future....

I need to know that how will i access my Win XP in case the Ubuntu fails and i loose the GRUB...

How will i re-install ubuntu to get back my dual boot

pkj

---

### Post by LaRoza on 2007-08-14
You have several option:

* Get the Super Grub Disk to restore the Windows MBR (it works like dream), link in my sig
* Install Ubuntu next to Windows, Ubuntu will add Windows to the new Grub.
* Reinstall Grub, not really the best option if you don't have Ubuntu or another OS.

---

### Post by ugm6hr on 2007-08-14
It depends on where you installed GRUB.

Try the following to find out:
Go to your BIOS, and select the Windows HD as first boot Hard drive.  Then boot.

If it boots to Windows, then you have no problem.  If/when the Ubuntu HD dies - just change the boot order as above, and Windows will work.

If it still boots GRUB, then your best option is to reinstall the Windows MBR on the Windows HD, and GRUB on the Ubuntu HD, and select the Ubuntu HD as first boot device in BIOS.
This shows how to restore Windows MBR: [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)
You'll have to search for how to restore GRUB.

---

### Post by pkj on 2007-08-14
Thanks

I will try the suggested options and get back to the forum for any further help required

pkj

---

