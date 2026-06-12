---
title: "laptob screen black - live cd"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by logicus on 2007-05-06
Hi there.
Yesterday, I was up at my mates flat and i wanted to show him the ubuntu live cd. Unfortunatedly, the screen was black and remained like that. Now, I can't tell you what computer he has cause he is leaving for london today but is there a general command or a set of commands you can use when you get a black screen ?

Sincerely

Peter

---

### Post by jiminycricket on 2007-05-06
If X crashed, you could try killing it with CTRL + ALT + BACKSPACE or CTRL + ALT + F1 and change to the vesa driver with sudo dpkg-reconfigure xserver-xorg  Do you know whether  it crashed at usplash?  Also try disabling acpi with the boot option editor from the grub menu, with noacpi or noapci or acpi=off.

Otherwise you could try an older CD like Dapper Drake (although that has some problems with some jmicron controllers I think).  Feisty Fawn had some changes with libata to libsata that affected some systems.

---

