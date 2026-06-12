---
title: "target disk question"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by adza on 2008-01-11
Hi there, can someone please explain something to me? I've installed a new HDD in my machine and the probe-scsi-all command gives the following (see screenshot)... my question is, the disk in target1 spot (middle line) is the one where the OS resides, how do i ensure that this is the one that is being set to boot off? really confused at the moment... ??

---

### Post by mikeyphi on 2008-01-11
> **adza said:**
> Hi there, can someone please explain something to me? I've installed a new HDD in my machine and the probe-scsi-all command gives the following (see screenshot)... my question is, the disk in target1 spot (middle line) is the one where the OS resides, how do i ensure that this is the one that is being set to boot off? really confused at the moment... ??

Not sure what problem you've got!

Do you see a 'Grub' page (text only) during the boot process just before the Ubuntu splash screen?

Are you trying to decide the Boot order for Hard drives to set in the Bios?

If you look at /boot/grub/menu.lst
you should see which hard drive is set as hd0,0

---

