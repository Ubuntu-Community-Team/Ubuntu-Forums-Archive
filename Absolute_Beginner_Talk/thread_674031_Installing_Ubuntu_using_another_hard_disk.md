---
title: "Installing Ubuntu using another hard disk"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by f0olyc0oly on 2008-01-21
how can i install ubuntu using another hard disk? because my primary hard disk is already full. and if I install ubuntu to the other hd will it erase the files there? :confused:

---

### Post by Aurora@FleetBuzz on 2008-01-21
Excellent resource here:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by f0olyc0oly on 2008-01-22
thnx. umm, one more question. what's a grub? do i need it to install the ubuntu?

---

### Post by mikeyphi on 2008-01-22
> **f0olyc0oly said:**
> thnx. umm, one more question. what's a grub? do i need it to install the ubuntu?

GRUB = bootloader, it looks for other OSs on your system and then changes the MBR to allow you to choose which OS you boot into - a good option, it shows you a text page during the boot process - if you don't make a choice it automatically loads the default OS - usually the last one you installed.
Most people with more than one OS eg Windows, Ubuntu etc happily use the GRUB. The only possible issue is if you also have windows and, at a later date, want a windows-only system - in that case you will need to fix the MBR but that is not difficult!!

---

### Post by caravel on 2008-01-22
Your system should have a boot menu in the BIOS where you can hit a key, usually F8 to select which disk you want to boot from.  This way you can dual boot but leave the windows boot sector untouched.

---

