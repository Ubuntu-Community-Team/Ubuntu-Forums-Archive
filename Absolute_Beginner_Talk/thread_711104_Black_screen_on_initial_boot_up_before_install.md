---
title: "Black screen on initial boot up before install"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Angry Dog on 2008-02-29
Hi,

I tried to install Ubuntu 7.10 on to my Fujitsu Siemens L7310 laptop.

It gave me a black screen before the installation.

I rebooted and tried it in safe graphics mode.

This gave me a flickering screen, but one i couldnt use.

is there a way to get it in proper vesa mode so i can at least get it installed?

thanks

---

### Post by miesnerd on 2008-02-29
if its just giving you a black screen, try hitting  Alt + F1. Seems especially prevalent on laptops. Usually its just taking longer to boot, and you can watch it boot.

---

### Post by dstew on 2008-02-29
At the first screen, type F6. That will let you add parameters to the kernel line that might let you use the Live CD. Commonly tried kernel parameters include vga=791 vesa=force acpi=off noapic nolapic irqpoll.

---

