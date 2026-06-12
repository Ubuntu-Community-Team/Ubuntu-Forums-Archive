---
title: "Vista/Feisty Dualboot"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Squizz on 2007-11-11
I've read through a few similar threads on here, and tried a few combinations but to no avail - and I started a new thread as I didn't want to hijack anyone elses.

I usually run Vista Ultimate, but I installed Feisty AMD64 earlier as I assumed that there would be a dual boot option by default.  I'm completely new to linux too.

Here's some info for you...
```

sudo fdisk -l

Disk /dev/hda: 82.3 GB, 82348277760 bytes
240 heads, 63 sectors/track, 10637 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10636    80408128+   7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19271   154794276   83  Linux
/dev/sda2           19272       19457     1494045    5  Extended
/dev/sda5           19272       19457     1494013+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390706232    b  W95 FAT32
```

Vista is installed on the 80gig HD - Feisty is on the 160gig one and the 400gig one is external.

```
cat /boot/grub/menu.lst

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=a807420b-d4c3-4e44-98a3-02d4bec213c2 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=a807420b-d4c3-4e44-98a3-02d4bec213c2 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=a807420b-d4c3-4e44-98a3-02d4bec213c2 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=a807420b-d4c3-4e44-98a3-02d4bec213c2 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

title Windows Vista
rootnoverify (hd0,1)
savedefault
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I added the Windows Vista bit to menu.lst myself - but obviously I haven't got much of a clue what I'm doing - just trying to piece things together.

Anyone got a quick fix?

Thanks very much in advance :)

---

### Post by meierfra on 2007-11-11
It should be:

title Windows Vista
rootnoverify (hd0,0)
savedefault
chainloader +1

(Grub starts counting at 0. So (hd0,0) stands for the first partition on the first hard drive)

---

### Post by Squizz on 2007-11-11
I'd just rebooted with that configuration :)

Thanks for the explanation though, it makes more sense that way.

I don't suppose there's a way to make the GRUB countdown longer?

---

### Post by meierfra on 2007-11-11
there is:

change

timeout 3    (I guess its 3, but it could be a different number)

in menu.lst to

timeout 10

Also   you might want to change 

#hiddenmenu

to 

hiddenmenu

---

### Post by Squizz on 2007-11-12
Excellent - thank you very much.

Got to love this community already!

---

