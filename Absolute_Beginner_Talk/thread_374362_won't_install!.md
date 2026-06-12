---
title: "won't install!"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by revmonkey on 2007-03-02
hi, i'm running a dell a1324n, ati radeon x200 gfx card on a hp vs19e monitor. when i try to install, it gives me 640x480 resolution, but that cuts off most of the screen so i can't see anything. i've tried to change the resolution on the live cd but it doesnt work. i've tried changing the resolution from "VGA" to just about everything else at the boot menu, but then it says the "frequency is out of range" on my monitor. is there any way to fix this? i'm not really technically inclined at all.

also, will i be able to choose between xp or ubuntu at startup? i know that i can choose between XP and recovery at startup... will ubuntu become a choice? again, i have little to no knowledge of the workings of ubuntu. thanks!
Edit/Delete Message

---

### Post by Sitix on 2007-03-02
First of all, yes, you will get a GRUB menu installed. That is a bootloader that allows you to choose your OS, in your case probably Ubuntu or XP.

The other problem, I would suggest to use the alternate install CD. You can download it only a few pixels away from the regular installation CD ;) Perhaps that works better as it is a DOS-like interface (to stick to windows terms :P)

---

### Post by revmonkey on 2007-03-16
bump?

---

### Post by zvacet on 2007-03-17
With alternate Cd you can install,because it´s in text mode.When you finish installation and reboot go to the terminal and type
```
 sudo dpkg-reconfigure xserver-xorg
```
pick** vesa** driver and your resolution supose to be fine.After that search for ati drivers and how to install it.

---

