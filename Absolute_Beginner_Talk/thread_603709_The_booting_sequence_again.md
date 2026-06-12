---
title: "The booting sequence again"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by nichos on 2007-11-05
In trying get XP booting 1st, I ended up with 2sets of Ubuntu choices. Tried them & both boot Ubuntu.:lolflag:

Now, can I delete one of them, say the 1st red set, & changind the "default" No. to suit, without loosing my PC again?       NICK


## ## End Default Options ##

[COLOR="Red"]title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ee66d6dd-05e0-4c06-9575-0471269905b9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ee66d6dd-05e0-4c06-9575-0471269905b9 ro single
initrd		/boot/initrd.img-2.6.20-16-generic[/COLOR]

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ee66d6dd-05e0-4c06-9575-0471269905b9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ee66d6dd-05e0-4c06-9575-0471269905b9 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:

---

### Post by overdrank on 2007-11-05
> **nichos said:**
> ```
In trying get XP booting 1st, I ended up with 2sets of Ubuntu choices. Tried them & both boot Ubuntu.:lolflag:

Now, can I delete one of them, say the 1st red set, & changind the "default" No. to suit, without loosing my PC again?       NICK


## ## End Default Options ##

[COLOR="Red"]title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ee66d6dd-05e0-4c06-9575-0471269905b9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ee66d6dd-05e0-4c06-9575-0471269905b9 ro single
initrd		/boot/initrd.img-2.6.20-16-generic[/COLOR]

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ee66d6dd-05e0-4c06-9575-0471269905b9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ee66d6dd-05e0-4c06-9575-0471269905b9 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
```

HI don't delete anything just place a # in front of the ones you don't want to view in the grub. This link may help
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by nichos on 2007-11-05
Thanx Pal, so that's what those jiberish crosses mean, and by the way dont drink too much.
nick

---

