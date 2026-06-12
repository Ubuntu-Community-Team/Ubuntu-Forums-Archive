---
title: "Dual-boot problem"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by AirAshby on 2007-02-16
My current menu.lst looks like this
```
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

title		Windows XP(Catia)
# root		(hd0,1)
makeactive
chainloader	+1

title		Windows Vista
root		(hd0,2)
makeactive
chainloader	+1
```
But neither of the Windows partitions will boot. Can someone please help me cause I need my Windows XP(Catia) for uni work that needs to be in in a couple of weeks.

---

### Post by mikewhatever on 2007-02-16
Can you also post the output of sudo fdisk -l

---

### Post by AirAshby on 2007-02-16
Here is the result of 
```
sudo fdisk -l
```
 ```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1828    14683378+  83  Linux
/dev/sda2            1829        3133    10482412+   f  W95 Ext'd (LBA)
/dev/sda3            3134        9660    52428127+  17  Hidden HPFS/NTFS
/dev/sda4            9661        9729      554242+  82  Linux swap / Solaris
/dev/sda5            1829        3133    10482381    7  HPFS/NTFS
```

---

### Post by dannyboy79 on 2007-02-16
you need to follow this one for tri-booting. good luck

[http://ubuntuforums.org/showthread.php?t=220452&highlight=tri+boot+vista](http://ubuntuforums.org/showthread.php?t=220452&highlight=tri+boot+vista)

---

### Post by mikewhatever on 2007-02-16
Can it be unhappy because one of the lines is commented out?
> title		Windows XP(Catia)
# root		(hd0,1)
makeactive
chainloader	+1

The '#' shouldn't be there. Do you get any errors trying to boot Windows?

---

### Post by dannyboy79 on 2007-02-16
> **mikewhatever said:**
> Can it be unhappy because one of the lines is commented out?


The '#' shouldn't be there. Do you get any errors trying to boot Windows?

well he just needs to check out the link I posted. Also, his grub lines aren't reading the correct partition anyway, his catia version of xp is calling for partition 2 which is a extended partition, which is W95 Ext'd (LBA). so that needs to be changed but also yes, you are probably right on the # symbol, but he just needs to follow that guide and he'll get it.

---

