---
title: "More Booting problems"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by KGH on 2006-08-21
I have XP on my SATA drive, Ubuntu & Mepis on my IDE drive. The boot grub is installed on sda.I can boot into both Linux OS with no problems. However I can't boot into XP

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		MEPIS at hdc1, kernel 2.6.15-26-386 (on /dev/hdc1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 nomce quiet vga=normal 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		MEMTEST (on /dev/hdc1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd1) (hd0)
map		(hd0) (hd1)
chainloader	+1

I swapped drive numbers on Ubuntu & Mepis in order to get them to boot.

Following the dual booting thread in the read this before you post I swapped drive numbers in the map lines.

What can I try next????

](*,) KGH

---

### Post by TFX360 on 2006-08-21
Dear KGH,


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1


Works like a charm here, tried that?


Kind regards,


TFX

---

### Post by KGH on 2006-08-23
I'm not sure why but I had to re-install XP and then re-install the grub menu. After changing the drive for XP to hd(0,0) it booted fine. 

KGH

---

### Post by TFX360 on 2006-08-24
Mmm maybe you should e-mail yourself a backup menu.list to yourself. For future reference!


Kind regards,


TFX

---

