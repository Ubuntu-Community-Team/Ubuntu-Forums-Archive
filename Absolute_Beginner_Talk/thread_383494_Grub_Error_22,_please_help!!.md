---
title: "Grub Error 22, please help!!"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by gameman12 on 2007-03-13
hello all, 

i've had a bunch of grub issues in the past and fixed them with forum help.(thx anybody who helped). 

i noticed in my linux install that i had stupidly installed ubuntu to the wrong partition. it was only about 5 gb, with 80mb free. that freaked me out. i noticed the intended partition was still there, so i popped in my gparted cd and deleted the unused partiton and increased my ubuntu partition with the remeaning space. obviously a dumb idea because i think i misread something and erased a linux partition.

anyway, i booted back up and got

Grub loading stage 1.5
grub error 22

and i'm not sure what to do next..... :-k help plz!

---

### Post by Cannonade on 2007-03-13
Could you post more information on your system set up please.

ie. Hard disc drive set up, mappings, etc. And if you are dual booting with XP or another Linux distro.

---

### Post by gameman12 on 2007-03-13
sry, my bad

i  can tell you so far i am dual booting with xp and ubuntu. i orginally tried installing grub onto my internal harddrive, but realized i need the external harddrive to boot into xp anyway. so this time i installed grub onto my external harddrive (should have  said earlier that the external drive has ubuntu and grub) 

brb with outputs of fdisk commands

---

### Post by gameman12 on 2007-03-13
ok here are the outputs of

```
fdisk -l
```

```
ubuntu@ubuntu:~$ fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24470   196555243+   7  HPFS/NTFS
/dev/sda4           24471       30401    47640757+   5  Extended
/dev/sda5           30378       30401      192748+  82  Linux swap / Solaris

Disk /dev/sdb: 64 MB, 64487424 bytes
4 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 128 * 512 = 65536 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         983       62896    b  W95 FAT32

```

---

### Post by dstew on 2007-03-13
Your linux install is indeed missing. Only the swap partition remains. You will need to create a new partition on your sda disk and re-install linux.

---

### Post by gameman12 on 2007-03-13
ok thx, i thought so, but didn't want to assume the worst.

thx for the help

---

