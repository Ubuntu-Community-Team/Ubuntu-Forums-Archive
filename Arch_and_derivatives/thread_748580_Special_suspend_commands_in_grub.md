---
title: "Special suspend commands in grub?"
date: 2008-04-07
forum: Arch and derivatives
---

### Post by PurposeOfReason on 2008-04-07
For a sucuessful suspend I need to run "pm-suspend --quirk-s3-bios --quirk-s3-mode" and I read that someone put "acpi_sleep=s3_bios" to the kernel line in their Grub. How would I go about doing this with my variables, or put them anywhere so they are default when I suspend with gnome-power-manager, lid close, etc.

---

### Post by fwojciec on 2008-04-07
Just edit /boot/grub/menu.lst and add this to the line that begins with "kernel" -- so it looks something like this:
> kernel /boot/vmlinuz26 root=/dev/sdb3 ro acpi_sleep=s3_bios

---

### Post by PurposeOfReason on 2008-04-07
> **fwojciec said:**
> Just edit /boot/grub/menu.lst and add this to the line that begins with "kernel" -- so it looks something like this:
So for the others would it be
```
 kernel /boot/vmlinuz26 root=/dev/sdb3 ro quirk-s3-bios quirk-s3-mode
```

---

### Post by fwojciec on 2008-04-07
I don't know what the guide you've read told you to do, but I'm pretty sure the "quirk" options are supposed to be used with pm-suspend command only (i.e. they shouldn't be added to the kernel line in menu.lst).

---

### Post by PurposeOfReason on 2008-04-07
I'm not sure. I'm just trying to find a way to make those variables default so it all works correctly.

---

### Post by fwojciec on 2008-04-07
I think that in order to have those quirks be selected by default you have to create "/etc/pm/config.d/config" file with the following contents:
> DISPLAY_QUIRK_S3_BIOS="true"
DISPLAY_QUIRK_S3_MODE="true"
Or something like that anyways...

---

### Post by PurposeOfReason on 2008-04-07
By George, I've wanted that for so long. Thanks! :KS

---

