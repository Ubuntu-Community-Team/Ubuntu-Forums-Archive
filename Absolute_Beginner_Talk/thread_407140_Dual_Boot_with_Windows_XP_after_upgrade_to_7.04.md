---
title: "Dual Boot with Windows XP after upgrade to 7.04"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by sarmax on 2007-04-11
I had setup my system with a dual boot with Ubuntu 6.10 and XP which had been working fine for sometime. I have the one hard disk which I had partioned 50:50 to Ubuntu and XP. I upgraded the 6.10 to 7.04 and now when I choose the XP option on the Grub menu XP begins to boot but just hangs. Any ideas ?

---

### Post by Stickymaddness on 2007-04-11
Where exactly does it hang? Is your windows partition still intact?

---

### Post by sarmax on 2007-04-11
The start up bars on the bottom of the screen complete OK and the XP logo screen starts up but after a few seconds the screen goes black (and stays black).

All of the partitions are intact.

---

### Post by confused57 on 2007-04-11
> **sarmax said:**
> The start up bars on the bottom of the screen complete OK and the XP logo screen starts up but after a few seconds the screen goes black (and stays black).

All of the partitions are intact.

May help if you can post the output of:
```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list
and
```
sudo fisk -l
```
the -l is a small "L"

Grub can always be reinstalled with the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

This website page has some excellent info about grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

