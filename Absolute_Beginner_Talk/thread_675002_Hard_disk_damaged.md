---
title: "Hard disk damaged"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by satjat on 2008-01-22
My Ubuntu hard disk started having problems today and I can no longer boot it.
Is there anyway to boot from the livecd, backup what might be rescued on a usb hard drive and then replace the disk?
I especially talk about installed packages, user settings and grub configuration...

Thank you all in adance, you might just save my life...

---

### Post by A4006 on 2008-01-22
You can burn a CD with all the files located in /var/cache/apt/archive and then load the CD in Synaptic upon your re-installation.  User settings I'm not so sure about, perhaps you could leave your old disk installed when you put your new HDD in, and then when you install Ubuntu to your new HDD, it would allow you to import user settings and accounts.  Your GRUB configuration should be the same as it currently is when you reinstall Ubuntu, because GRUB automatically looks for bootable operating systems.  If you have one IDE and one SATA drive, you might run into some issues if you leave them both installed, just make sure you get GRUB installed to the right drive.

---

### Post by mikeyphi on 2008-01-22
> **satjat said:**
> My Ubuntu hard disk started having problems today and I can no longer boot it.
Is there anyway to boot from the livecd, backup what might be rescued on a usb hard drive and then replace the disk?
I especially talk about installed packages, user settings and grub configuration...

Thank you all in adance, you might just save my life...

If your disk is still working but has only lost the boot file - you might try booting from the LiveCD and downloading testdisk through Synaptic....use that to get a better idea of your problem.

---

