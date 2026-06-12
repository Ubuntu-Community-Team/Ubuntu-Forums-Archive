---
title: "Help!  Grub not recognizing my Edgy install"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by MakLeod on 2006-11-10
Just installed Edgy onto the same drive as my Dapper installation, but Grub does not recognize the new Edgy install.  How would I go about finding which hd parameters e.g. (hd0,1) my new Edgy install is on.  And then after that how would I append Grub to see it?

---

### Post by bulldog on 2006-11-10
Type ```
sudo fdisk -l (l as in like)
``` and see what partitions you have.

---

### Post by MakLeod on 2006-11-10
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       26198   210435403+  83  Linux
/dev/sda2           27474       28898    11446312+   7  HPFS/NTFS
/dev/sda3           28899       30401    12072847+   5  Extended
/dev/sda4           26199       27473    10241437+  83  Linux
/dev/sda5           30024       30401     3036253+  82  Linux swap / Solaris
/dev/sda6   *       28899       29972     8626842   83  Linux
/dev/sda7           29973       30023      409626   82  Linux swap / Solaris

Partition table entries are not in disk order


Now the Edgy install is on /dev/sda6, but I don't know the parameters for it in Grub.  I am going to try hd(0,2) and see what happens.

---

### Post by MakLeod on 2006-11-10
Well, hd(0,2) didn't work...wonder where it's hiding =)

---

### Post by bulldog on 2006-11-10
Can you give me a copy of your menu.lst?

```
gedit /boot/grub/menu.lst
```

I think it should be something like this```

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot
```

[You made two swap files,that's overkill,you can do it with one!]

---

