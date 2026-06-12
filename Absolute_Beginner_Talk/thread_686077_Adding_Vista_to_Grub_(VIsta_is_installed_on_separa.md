---
title: "Adding Vista to Grub (VIsta is installed on separate partitions, but unrecognized)"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by mfitzmorris on 2008-02-02
Well, after installing Ubuntu 6.06 (most compatible with my Compaq F500 laptop) into the  approx. 8gb free space of my laptop, which already has Vista installed on the 65gb, main partition, Grub fails to recognize my original Vista partition. Does anyone know how to add this bootup info to Grub? Many thanks in advance!

EDIT: While editing menu.lst, the system will not allow me to save the modified version. What is the simplest way to do so? Thanks!

Results of cat /boot/grub/menu.lst

```
title           Ubuntu, kernel 2.6.15-26-amd64-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda2 ro quiet splash noapic
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot
```

Results of sudo fdisk -l

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8528    68494863+   7  HPFS/NTFS
/dev/sda2   *        8529        9675     9213277+  83  Linux
/dev/sda3            9676        9729      433755    5  Extended
/dev/sda5            9676        9729      433723+  82  Linux swap / Solaris

```

---

### Post by overdrank on 2008-02-02
Hi and this link may help 
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
And when editing the list you can use this command ```
gksudo gedit /boot/grub/menu.lst
```

---

