---
title: "Grub overwrites Windows Vista"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by jeffreyvergara.NET on 2005-12-20
Hello, im trying out window$ vista this afternoon, I setup the partition like what I did in Window$ XP, Install XP then Install Ubuntu, Grub auto detects Window$ XP, and I have no problem at all.
I went to try vista, I did setup exactly the same but Grub did not detect Vista.

How do I add Window$ Vista on the menu. 
> sudo gedit /boot/grub/menu.lst

What should I add here:
> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by manicka on 2005-12-20
Try adding something like this

### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Ubuntu
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Vista
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

