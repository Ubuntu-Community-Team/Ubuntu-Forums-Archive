---
title: "Grub messed up!!!"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by eoghanmurray on 2007-06-28
I followed a guide to make a graphical grub loader. it fai ed and i can't boot. every option i choose reports cannot boot from selected partition - plz help! using pocket pc btw.

---

### Post by dexter on 2007-06-28
- What guide did you follow ?
- Can you post your /boot/grub/menu.lst file ? If you can't start up your computer try using the Ubuntu live disk.

---

### Post by eoghanmurray on 2007-06-28
I'll try to get them tomorrow - battery at 3% lol

---

### Post by eoghanmurray on 2007-06-29
OK Talk me through this - i cannot boot my computer via hard disk. on pocket pc atm. shpuld i use live cd?

---

### Post by hyper_ch on 2007-06-29
yes, use the livecd...

Btw, do you have SATA and IDE drives in your computer?

---

### Post by eoghanmurray on 2007-06-29
just 1 sata internal - 1 usb external which has ubuntu installation on it

ok live cd loaded

---

### Post by eoghanmurray on 2007-06-29
what if...
if i can find my xp disk, could i run recovery console to restore master boot record? then boot into xp and use paragon disk manager to restore linux's mbr?

---

### Post by eoghanmurray on 2007-06-29
fixed! all working now! ty everyone !

---

### Post by eoghanmurray on 2007-06-29
oh no - only worked once!
how do i restore grub fRom live cd?

---

### Post by confused57 on 2007-06-29
> **eoghanmurray said:**
> oh no - only worked once!
how do i restore grub fRom live cd?

You can mount your root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
access your menu.lst, then you should be able to just comment out anything relating to a grub splash screen....

You can reinstall grub with the live cd, also:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

