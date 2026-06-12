---
title: "how do i make grub my default bootloader?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by sircatsbythe3rd on 2007-07-11
ok, im having this one irritating problem that i cant seem to fix. for some reason grub doesn't boot up by default and i always get the windows ntdlr bootloader, which is on my secondary sata drive. the only way i can get to grub is by manually go to the boot menu on my bios and picking my primary master drive to boot. 

i don't know how or why my boot loader is on my secondary drive because both my ubuntu os and xp is on my primary master drive. 

so does anyone know how to remove the windows bootloader and make grub my default?

---

### Post by bodhi.zazen on 2007-07-11
You need to install GRUB into the MBR.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by sircatsbythe3rd on 2007-07-11
thanks!!! that did the trick.

---

