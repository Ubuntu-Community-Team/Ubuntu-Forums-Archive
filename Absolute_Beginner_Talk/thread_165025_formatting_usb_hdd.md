---
title: "formatting usb hdd"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by BLZPLZ on 2006-04-23
k i have a usb hdd i was wondering if there where instructions on how i could format it using fdisk
i cant get gpartedbecause i cant install new packages with my synaptic bugged as it is

im going to reinstall ubuntu and dual boot it with win xp

so yah just some instructions on using fdisk to format the usb hdd

---

### Post by BLZPLZ on 2006-04-23
8 views and not one help??

---

### Post by Sutekh on 2006-04-23
Try using the man pages on your PC for general usage
```
man fdisk
```

[Man Page for fdisk](http://www.die.net/doc/linux/man/man8/fdisk.8.html)

and check out parted too (not GParted)
```
man parted
```

[Parted Manual](http://www.gnu.org/software/parted/manual/html_mono/parted.html)

Edit: The Ubuntu installer disk can also handle formatting (it uses parted I think)

---

### Post by dave9191 on 2006-04-23
fdisk is not a program for formatting partions. It is a programs used for making partions. So if you want to split your usb hdd into several partions (or drives if you prefer) then you need fdisk. If you just want to format your usb hdd then you need another program depending on the file system you want to create. 

mkfs.ext3      mkfs.msdos     mkfs.vfat
mkfs.cramfs    mkfs.jfs       mkfs.reiser4   mkfs.xfs
mkfs.ext2      mkfs.minix     mkfs.reiserfs

Look at the man page for mkfs (man mkfs) for details. Just be sure to spesify the correct drive to format or you could loose your data :)

--
Dave

---

