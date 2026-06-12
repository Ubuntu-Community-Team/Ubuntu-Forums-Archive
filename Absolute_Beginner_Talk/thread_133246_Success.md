---
title: "Success???"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by jasrog on 2006-02-19
I just did a dual boot installation and was wondering if there is a command I can do and then copy and paste to this thread and have someone look at it and tell me if I have a good configuration?

---

### Post by Zeroangel on 2006-02-19
```
sudo gedit /boot/grub/menu.lst
```

Copy/Paste the bottom of your file into your post. Like so:
> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by az on 2006-02-19
[QUOTE=jasrog]I just did a dual boot installation and was wondering if there is a command I can do and then copy and paste to this thread and have someone look at it and tell me if I have a good configuration?[/QUOTE]

A configuration for what, specifically?

---

### Post by jasrog on 2006-02-19
basically I want to know what amount of space I have to use for files,music,programs...exc after i set up dual boot on my pc? I look at my drives in gparted but am confused what is available...

---

### Post by az on 2006-02-19
Click on System - Administration - Disks.

That will tell you how big each of your partitions are.

---

### Post by Zeroangel on 2006-02-19
You can also go to Applications > System TOOLs > System Monitor

---

