---
title: "ubuntu not loading"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by default00 on 2008-03-20
i have xp and ubuntu installed on my laptop and after messing around on ubuntu a little bit i rebooted my computer. when ubuntu tries to load i get an error saying: 

bcm43xx: Error: Microcode "bcm43xx_microcode.fw" not available or load failed

do i have to install a fresh copy of ubuntu or can i fix this? thanks

---

### Post by athaki on 2008-03-20
Try a fresh install.

---

### Post by OhioYJ on 2008-03-20
Did you have your wireless working in Ubuntu?

Perhaps booting into the recovery option of Ubuntu and blacklisting the bcm43xx driver, temporarily to get it booted, then reinstall it if you need it for your wireless card.

Where you doing anything in particular before this happened, such as using a script to load your wireless drivers?

---

### Post by keratos on 2008-03-20
> **athaki said:**
> Try a fresh install.

thats rather extreme.

Erm, try adding the arguments " pci=routeirq" to the kernel boot command. So when booting (GRUB I assume) select 'e' to edit the 'kernel' line and add those arguments (no quotes and dont forget the first spae)

Failing that, disable APIC/APM/PM  in the BIOS.

---

### Post by default00 on 2008-03-20
oops too late. put on a fresh install. only had it for a little bit so fresh install wasnt a big deal. thanks for the help incase of future problems.

---

