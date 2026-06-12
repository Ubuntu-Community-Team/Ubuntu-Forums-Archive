---
title: "Asus q500a-bsi5n04"
date: 2013-08-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by tahdas on 2013-08-16
I  thinking about getting the asus q500a and im wondering how hard it would be to put Ubuntu on.
Also is this computer a good buy? Will last at leats four years? Can I play a few games on it?
thanks
tahdas

---

### Post by tahdas on 2013-08-17
Bump!

---

### Post by seth4 on 2013-08-24
I have an asus q500a with ubuntu. Been running it for at least a month. Computer runs a bit hot, probably because of quad core processor. Overall, it is a great computer. The touchscreen immediately worked perfect from a live disk. Experiencing weird keyboard problems and sometimes the mouse malfunctions and wants to grab things instead of click. ctrl alt del is the only way I have been able to get out of this because when it happens I cannot type commands into the terminal. I will post something on this which you can refer to for more details. Anyway, after some trouble I got a dual boot with win 8 working just fine. Tap delete at startup, disable secure boot, and enabled launch csm/pxe OpRom(not sure what this is or if it was necessary). Cannot remember exactly but you will find it if you look around in bios. Once both os are on there you can switch between them in temporary boot device manager. Boot to ubuntu, install and run startup repair utility (can find in software center) just go with the standard repair that it will want to run. I did this from a live disk because I manually upgraded to grub 2 and did a update-grub which somehow prevented me from booting. Just use the boot repair utility with the standard proceedures and it should work just fine and give you a windows uefi boot in grub menu!

---

