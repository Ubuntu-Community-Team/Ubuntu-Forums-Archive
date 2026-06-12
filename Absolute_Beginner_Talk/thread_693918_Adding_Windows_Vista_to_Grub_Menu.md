---
title: "Adding Windows Vista to Grub Menu"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by dnguyen1022 on 2008-02-11
Hello guys, I would like to know how to add windows vista to my grub menu.  I have ubuntu installed on an external hd.  This is what I have from menu.lst

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9460a08b

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 234438655 117218304 7 HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

Device Boot Start End Blocks Id System
/dev/sdb1 * 63 97659134 48829536 83 Linux
/dev/sdb2 97660928 486430719 194384896 7 HPFS/NTFS
/dev/sdb3 486432135 488392064 979965 5 Extended
/dev/sdb5 486432198 488392064 979933+ 82 Linux swap / Solaris

---

### Post by spiderbatdad on 2008-02-11
that looks like an fdisk -l output. ```
cat /boot/grub/menu.lst
```

---

### Post by Ek0nomik on 2008-02-11
Add the following to your menu.lst:

```
title         "Windows Vista"
root         (hd0,0)
makeactive
chainloader      +1
```

---

### Post by dnguyen1022 on 2008-02-13
mmm that didnt work...heres the cat file thing

title           Ubuntu 7.10, kernel 2.6.24-5-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-5-generic root=UUID=8af2de56-262c-4a04-8926-0fe48b73faf9 ro quiet splash
initrd          /boot/initrd.img-2.6.24-5-generic
quiet

title           Ubuntu 7.10, kernel 2.6.24-5-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-5-generic root=UUID=8af2de56-262c-4a04-8926-0fe48b73faf9 ro single
initrd          /boot/initrd.img-2.6.24-5-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8af2de56-262c-4a04-8926-0fe48b73faf9 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8af2de56-262c-4a04-8926-0fe48b73faf9 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

---

### Post by Ek0nomik on 2008-02-13
> **dnguyen1022 said:**
> mmm that didnt work...heres the cat file thing

title           Ubuntu 7.10, kernel 2.6.24-5-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-5-generic root=UUID=8af2de56-262c-4a04-8926-0fe48b73faf9 ro quiet splash
initrd          /boot/initrd.img-2.6.24-5-generic
quiet

title           Ubuntu 7.10, kernel 2.6.24-5-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-5-generic root=UUID=8af2de56-262c-4a04-8926-0fe48b73faf9 ro single
initrd          /boot/initrd.img-2.6.24-5-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8af2de56-262c-4a04-8926-0fe48b73faf9 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8af2de56-262c-4a04-8926-0fe48b73faf9 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

You never added what I had posted into your menu.lst file.  However, based on your fdisk -l output, it looks like you have two partitions formatted as NTFS.  Is Vista installed on the 120GB or 250GB hard drive?

---

### Post by dnguyen1022 on 2008-02-19
vista is on the 120gb, i believe i did add it though.  linux is installed on the 250gb(external)

---

### Post by dnguyen1022 on 2008-02-22
title           Ubuntu 7.10, kernel 2.6.24-5-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-5-generic root=UUID=8af2de56-262c-4a04-8926-0fe48b73faf9 ro quiet splash
initrd          /boot/initrd.img-2.6.24-5-generic
quiet

title           Ubuntu 7.10, kernel 2.6.24-5-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-5-generic root=UUID=8af2de56-262c-4a04-8926-0fe48b73faf9 ro single
initrd          /boot/initrd.img-2.6.24-5-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8af2de56-262c-4a04-8926-0fe48b73faf9 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8af2de56-262c-4a04-8926-0fe48b73faf9 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

title         "Windows Vista"
root          (hd0,0)
makeactive
chainloader      +1
### END DEBIAN AUTOMAGIC KERNELS LIST


ok im sure i added it now but it still does not work..something about unsupported..cant recall the error message

---

### Post by zxscooby on 2008-02-22
According to you menu.lst everything is on the same partition.

Try reading this page, its very helpful.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by dnguyen1022 on 2008-02-22
so would it work if i changed it to hd(1, 0) as my windows is in my internal hard drive, and it sees my external as my first(hd(0,0))?

---

