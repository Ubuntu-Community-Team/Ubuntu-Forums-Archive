---
title: "Ubuntu won't load (GRUB error 15)!"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by playing_with_matches on 2007-03-28
Hello all,
I searched the forums, and tried the suggestions, but they don't seem to work.
I recently tried to increase my partition size for my Ubuntu partition (I had to copy and paste the partion using Gparted... then increase the size), and now I get Error 15 (Missing File) when I try to boot Ubuntu through GRUB.

When I Fdisk:

```
/dev/hda1   *           1        2555    20523006    c  W95 FAT32 (LBA)
/dev/hda2            2556        7299    38106180    b  W95 FAT32

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       10011    80413326    b  W95 FAT32
/dev/hdb2   *       10012       19929    79666335   83  Linux

```

When I mount hdb2 (the partion ubuntu is on), I am able to completely access it, and the grub boot file looks like:

```
title           Ubuntu, kernel 2.6.17-11-generic
root           (hd1,1)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root           (hd1,1)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb2 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root          (hd1,1)
kernel       /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet
boot
```

the vmlinuz file is in the partion's boot folder.  I am really confused on what's wrong, and would rather not reinstall ubuntu completely.  Thanks for any help!!!

---

### Post by orb9220 on 2007-03-28
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by playing_with_matches on 2007-03-28
Thanks for responding.
I tried the things it said in the thread, and it still gives me grub error 15: Missing File.  Any other suggestions?

---

### Post by orb9220 on 2007-03-29
Did you install the grub to (hda0,0) or what ever is the first hd?

Even tho you install linux to a seperate hd you must install grub to the first Hd for the system to see the grub loader on bootup which will point to ubuntu on the second HD.

That is the only thing I can think of is that you are installing grub to the second Hd instead of to the first Hd.

---

