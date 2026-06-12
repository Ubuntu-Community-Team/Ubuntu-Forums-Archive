---
title: "Dual boot xp help"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by chd_lad on 2008-04-06
hi,
i already had xp sp2 on my sata hdd
i installed ubuntu 7.10 on my 2nd hdd a 80gb ide
the problem i am facing is that when i use ide hdd as first boot device the grub loader works. it lists the os options. but the xp option does not work.
when i select xp it takes me to a screen where it says 
Starting...
and it just sits there. any suggestions 

here are the contents of my menu.lst

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=8ec87dd1-7b9d-4d9c-b606-21a0b3a6de7a ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=8ec87dd1-7b9d-4d9c-b606-21a0b3a6de7a ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1


please help

---

### Post by kissson on 2008-04-06
try add and boot

title test
root (hd0,0)
#savedefault
#makeactive
chainloader +1

---

### Post by confused57 on 2008-04-06
You probably need map lines:
```
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

### Post by chd_lad on 2008-04-06
> **confused57 said:**
> You probably need map lines:
```
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

thanks a ton buddy
it works like a charm :)
btw what does map do? can you give some details about it?

---

### Post by Michael.Godawski on 2008-04-06
The map lines just simulate that windows is installed on the first drive so that it boots properly.Map tells Grub where to find things

---

### Post by chd_lad on 2008-04-07
> **Michael.Godawski said:**
> The map lines just simulate that windows is installed on the first drive so that it boots properly.Map tells Grub where to find things

thanks for the info

---

