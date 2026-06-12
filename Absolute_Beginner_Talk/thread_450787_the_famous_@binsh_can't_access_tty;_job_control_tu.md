---
title: "the famous @/bin/sh: can't access tty; job control turned off&quot;"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by kufio on 2007-05-21
I have ubuntu 6.06. It was running smoothly and it was well tuned for a long time. But this morning I got the famous "/bin/sh: can't access tty; job control turned off" . I am now on a live CD. I did not change the hardware and  this is my partition 

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9447    75882996   83  Linux
/dev/hda2            9448        9729     2265165    5  Extended
/dev/hda5            9448        9729     2265133+  82  Linux swap / Solaris

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               2        9729    78140160    f  W95 Ext'd (LBA)
/dev/hdc5               2        4880    39190536    b  W95 FAT32
/dev/hdc6            4881        9729    38949561    b  W95 FAT32

*and my grub list*

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by hartz on 2007-05-22
Hi there.

Please can you explain what you are doing when this is happening?  Are you running some software on the system console?

What changed before this?  Updated Kernel?  Installed Software?  New Graphics drivers?  New Virtual machines configured?  New hardware installed?

Could you perhaps provide screen-shots?

Could you provide the following command's output immediately after the error ocured:
```
dmesg|tail -30
```

---

