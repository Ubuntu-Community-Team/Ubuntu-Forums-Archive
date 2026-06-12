---
title: "Help adding Windows on SATA drive to GRUB"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by jordantbro on 2006-10-06
Here is my current sudo fdisk -l
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       10443    83875365    f  W95 Ext'd (LBA)
/dev/sda2           10444       14463    32290650   83  Linux
/dev/sda3           14464       14593     1044225   82  Linux swap / Solaris
/dev/sda5               2       10443    83875333+   7  HPFS/NTFS

```

Here is my current Windows section of GRUB
```
title		Microsoft Windows XP Professional
root		(hd0,5)
savedefault
makeactive
chainloader	+1
```

Ubuntu and Windows XP are on the same SATA drive.  There is only 1 drive in the laptop.

Basically I just need to get that 80 gig NTFS partition to show up in GRUB.  Any help is appreciated.

Jordan

---

### Post by jordantbro on 2006-10-06
Here is the full GRUB List
```
title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
bootcro

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

title		Microsoft Windows XP Professional
root		(hd0,5)
savedefault
makeactive
chainloader	+1
```

---

### Post by JayTee on 2006-10-06
I'd change the 5 to either 3 or 4 which is probably the correct logical partition nunber for Windows XP. The output of your fdisk -l is a bit confusing as it seems to skip an SDA4. I'm wondering if there is a partition that Linux isn't recognizing in fdisk. If you Linux install is loading ok it can't hurt to try modifying the partition number in the (HD0,#) area of the Windows section of the grub menu.lst file. You can always set it back to 5. If 5 is the correct partition number then and you can't boot Windows XP then the problem isn't with GRUB. When you choose that option what kind of loading errors are you getting?

---

### Post by jordantbro on 2006-10-07
Thanks for the reply.  I should mention that for whatever reason after I installed Ubuntu Windows was not even listed in GRUB.  I added all of the Windows info and it may be incorrect.  I have tried all of the (hd0,1) - (hd0,6).

---

### Post by jordantbro on 2006-10-07
BUMP.

Still looking for help on this one.

---

