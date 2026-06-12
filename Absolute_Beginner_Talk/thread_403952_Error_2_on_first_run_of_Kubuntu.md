---
title: "Error 2 on first run of Kubuntu"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by bwolper on 2007-04-07
[CENTER]**THIRD TIMES A CHARM?**[/CENTER]

I just installed Kubuntu 6.10 with the alt. installation disk. Everything seemed to well during the installation.

Upon booting my system I get "Grub loading stage1.5. the next line says "Grub loading, please wait. . . " the next line says "Error 2" and it just sits there.

What does this mean and what do I need to do from here?


CENTER]**THIRD TIMES A CHARM?**[/CENTER]

---

### Post by msaied on 2007-04-07
I did a quick search on GRUB Error Messages and found the flowing

Error 2 : "Selected disk doesn't exist"

This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

it might be related to this bug: [URL="I did a quick search on GRUB Error Messages and found the flowing

Error 2 : "Selected disk doesn't exist"

This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

it might be related to this bug: https://launchpad.net/ubuntu/+source/grub/+bug/17635"]https://launchpad.net/ubuntu/+source/grub/+bug/17635[/URL]

---

