---
title: "GRUB: Problem using WinXP and Ubuntu partitions"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by SuperBonk on 2007-04-29
Hi,

After buying a new hard disk, I decided to install Ubuntu and to use the grub bootloader for switching between my WinXP and Ubuntu partitions. Unfortunately, a problem occurs and after googling and experimenting for hours, literally, I still have no idea, what to do:

I have three hard disks. WinXP manages the first two (IDE and S-ATAII), Ubuntu the last one (S-ATAI). When I chose one of the partitions using BIOS, it works flawlessly. However, using grub leads to problems. 

The most confusing thing is the device mapping. Inside Ubuntu, the device.map is given as follows:

```

(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb

```

Since Ubuntu and grub were installed to sdb, WinXP into hda, I thought, the correct entries in menu.lst would be (according to the grub manual):

```

## ## End Default Options ##


title		     WinXP
root	           (hd0,0)
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=980c2af3-8059-480a-9453-7f29b780bf84 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet


title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=980c2af3-8059-480a-9453-7f29b780bf84 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

This configuration didn't work at all, neither WinXP or Ubuntu were bootable. Desperately, I tried lots of stuff. I assigned the Ubuntu stuff to (hd0,0) and Ubuntu worked (?). Then I tried every combination (hdx,y) for WinXP, but I always got errors and Win didn't boot:

error 13: Invalid or unsupported executable format
error 12: Invalid device requested

I also tried mapping with probably all combinations of map (hdx) (hdy) and map (hdy) (hdx) - all of them resulting in the same error messages - and now I'm out of ideas. It would be great, if You could help me.

eva

---

### Post by riminicat on 2007-04-29
Have you tried using a rescue disk to boot into your os's?  I couldn't boot after installing grub so I got an iso of a rescue disk and stuck it in the disk drive, then chose what os to boot into.

Good Luck and I hope that helped

---

### Post by Malta paul on 2007-04-29
Hi,
As Riminicat suggests you coul try a rescue disk.
I had a little problem when I upgraded to 7.04. I did a manual and clean partition on my second disk to protect my existing files. My root order was then mixed up in Grub.
My root is now hd0,3. I would say its the second number you need to find? You could reinstall Gparted and check your partition order.        Hope this may help :)

---

### Post by Sequent on 2007-04-29
Grub needs to be installed on the MBR of hda

---

### Post by riminicat on 2007-04-29
> **Sequent said:**
> Grub needs to be installed on the MBR of hda

This is true, but windows overwrites it sometimes so it should also be put on the linux partition so that it can be accessed from a rescue disk

---

