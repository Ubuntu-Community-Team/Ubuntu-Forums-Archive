---
title: "Help."
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by 1j1j1j256 on 2008-01-19
I dont know much about these things so... My dad says i have an windows xp installed in the computer (im using ubuntu now) however it is somehow hidden so ill have to configure my boot loader to make it boot that or something. so please help me to find out how.

---

### Post by cotcot on 2008-01-19
Your question is not very clear. I guess that you lost XP in the bootloader options ?
In case of [[COLOR="Red"]this[/COLOR]]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively") is a way to reinstall the bootloader.

---

### Post by kellemes on 2008-01-19
Assuming you have a working Grub-bootloader, so it's just that Windows isn't in the list, try the following from the terminal..

```
gksudo gedit /boot/grub/menu.lst
```

Add the following to the list...

```
title           Microsoft Windows
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

the line with (hd0,0) *may* have to be changed to your specific location of Windows.

---

