---
title: "booting trouble"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by dhirajkhanna on 2008-03-15
Hello I am having problems in booting up. Most of the times when I try to boot (Ubuntu 7.10) the screen just goes blank and that's it. After resetting the computer physically for 4 or 5 times, I sometimes get lucky. However, by booting through the recovery mode and then typing exit at the end of its operation, I am able to boot in normally. Some help here please.

---

### Post by dstew on 2008-03-15
At the grub screen, with the regular boot item highlighted, instead of enter, press 'e'. This gets you into edit mode. Use the up-down arrows to highlight the kernel line. Press 'e' again, and remove **quiet splash** from the end of the line. Press 'enter' to save, and then press 'b' to boot. If this works, you should see the kernel messages at boot time, instead of the Ubuntu splash screen. If it boots, fine, you can make the change permanent by editing your /boot/grub/menu.lst file, removing quiet splash from the kernel line. If it does not boot, you might be able to see errors that say why. If it does not boot after you remove quiet splash, post any errors you see to the forum.

---

