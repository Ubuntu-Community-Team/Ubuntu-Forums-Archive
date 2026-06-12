---
title: "Ubuntu 8.10 on a stick"
date: 2009-01-15
forum: Apple Hardware Users
---

### Post by jtheb on 2009-01-15
I am installing Ubuntu 8.10 on a flash drive. I am currently using 8.10 on a PC.

My wife has a Mac OS X current version and I want to know if it will boot from this USB stick.

Thanks

---

### Post by utnubuuser on 2009-01-15
Hi  --  Being able to boot from USB is a BIOS issue.  Most newer machines have native support for USB, slightly older ones require the user to enable USB support in BIOS, and most machines that are more than a few years old simply do not support it at all.

BIOS = F1 or F2, or esc+F1, or esc+F2 at start-up.

There are ways of enabling this functionality by using a minimal bootCD or floppy, but it's no small matter.

---

### Post by cyberdork33 on 2009-01-15
> **jtheb said:**
> I am installing Ubuntu 8.10 on a flash drive. I am currently using 8.10 on a PC.

My wife has a Mac OS X current version and I want to know if it will boot from this USB stick.
No, 
If she has a PPC Mac, then it will only boot a powerpc distro
If she has an Intel Mac, you might be able to get grub-efi working on it.

> **utnubuuser said:**
> Hi  --  Being able to boot from USB is a BIOS issue.  Most newer machines have native support for USB, slightly older ones require the user to enable USB support in BIOS, and most machines that are more than a few years old simply do not support it at all.

BIOS = F1 or F2, or esc+F1, or esc+F2 at start-up.

There are ways of enabling this functionality by using a minimal bootCD or floppy, but it's no small matter.Macs do not have a BIOS

On an Intel Mac, you can use a boot cd though:
[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/)

---

