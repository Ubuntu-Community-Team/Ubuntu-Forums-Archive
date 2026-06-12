---
title: "Dual Boot"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by tw0shoes on 2007-10-31
Just a quick issue w/ regards to my xp/gutsy dual boot. I installed xp after gutsy and after reloading grub xp doesn't appear on the menu list. 

sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1351    10851876   83  Linux
/dev/sda2   *        1352        1364      104422+   7  HPFS/NTFS
/dev/sda3            1365        4659    26467087+   7  HPFS/NTFS
/dev/sda4            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris


end of menu.lst:

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=590aaefe-d52f-455e-b5b1-dbd05833a9ee ro quiet 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=590aaefe-d52f-455e-b5b1-dbd05833a9ee ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

What do I need to add to the end exactly to allow for the windows boot option. 

Thanks.

---

### Post by khughitt on 2007-10-31
What are the results of typing **sudo /sbin/fdisk -l** in a terminal window?

---

### Post by skymera on 2007-10-31
well you have 2 NTFS partitions.

try 

```
 sudo update-grub 
```

---

### Post by Duck2006 on 2007-10-31
This may help you add windoze to your menu.lst

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by khughitt on 2007-10-31
Oh sorry, I was not paying attention and completely missed the fact that you already posted the results for fdisk. Try adding:

```

title        Windows
root        (hd0,1)
savedefault
makeactive
chainloader    +1

```

to your menu.lst file.

Goodluck,

---

### Post by tw0shoes on 2007-10-31
thanks so much for the help.

---

### Post by khughitt on 2007-10-31
Anytime :)

---

