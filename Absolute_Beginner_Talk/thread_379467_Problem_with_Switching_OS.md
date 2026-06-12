---
title: "Problem with Switching OS"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by nerds in parties on 2007-03-08
hello there. When i boot to windows everything works fine. but then when I try to boot to ubuntu it freezes at the startup loading. please help.

---

### Post by dstew on 2007-03-08
Do you have Ubuntu installed already, or are you trying to boot from a Live CD? Do you get an error message of some kind?

---

### Post by mikewhatever on 2007-03-08
Are there any error messages? Do you use GRUB as boot manager?

---

### Post by nerds in parties on 2007-03-08
> **dstew said:**
> Do you have Ubuntu installed already, or are you trying to boot from a Live CD? Do you get an error message of some kind?

no i have it already installed. but every time i was switching to windows at startup using Grub i had the same problem and i had to reformat/install ubuntu again and again.

---

### Post by nerds in parties on 2007-03-08
> **mikewhatever said:**
> Are there any error messages? Do you use GRUB as boot manager?

yes GRUB. to errors no nothing. it just freezes at ubuntu loading.

---

### Post by dannyboy79 on 2007-03-08
pop in the live cd, then mount your parititon that contains your /boot directory, then open your file called menu.lst located within /boot/grub/ then add the following at the end of the boot lines, at least the 1st choice so we can see if that does it. when linux is booting sometimes different hardware can make it freeze, if we try these options it can help sometimes.

kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro irqpoll noapic acpi=off

erase the splash and the quiet so we can see if there are any errors that appear during bootup. good luck. also, have you checked that your ram passed memtest. test each stick individually.

---

