---
title: "ACPI/APMD Problem"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Terman on 2007-04-01
I've installed 7.04 on a Dell Inspiron 7000, and do not understand how I can get it to turn off the power at shutdown.

During bootup, an ACPI - Unable to locate RSDP warning occurs, and the installer help file implies that a noacpi command should be added at the (boot) prompt. Unhelpfully, though, it doesn't mention where to find such a prompt.

How can I now amend the boot commands to disable ACPI and, I hope, enable APMD?

---

### Post by dstew on 2007-04-01
You can edit the /boot/grub/menu.lst file, and add the boot options at the end of the kernel line:

kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro quiet **acpi=off**

Of course, your kernel line will be different from mine. I could not find out how to use APMD. I don't know if it is enable by boot option, or some other way.

---

