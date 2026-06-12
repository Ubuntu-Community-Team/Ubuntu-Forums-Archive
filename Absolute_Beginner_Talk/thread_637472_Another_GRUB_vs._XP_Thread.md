---
title: "Another GRUB vs. XP Thread"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by RDonnelly on 2007-12-11
Hi everyone, I'm really sorry for making my first post another GRUB problem, but I really kind of need an answer relatively fast.  I've got a coding project to do for wednesday night and I'd like to get my stuff working right.

Anyway, I know I may have went about things weird, but the situation is that I have a big partition that I'd like to use for media between the dual-booted OS's.  I had my XP running well with all my stuff right, backed it up and then installed Ubuntu.  Now,  I can't Grub to my XP (suprising, I know!).  I've tried looking in threads and fixing it myself, but I think I'm gonna have to ask for help.  When I try to boot into my XP patition, it says "Starting..." but doesn't do anything after that.  Any tips or advice would be awesome.  Here's my fdisk output:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7649    61440560+   b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sda2            7650       19267    93321585    f  W95 Ext'd (LBA)
/dev/sda5   *        7650       13523    47182873+   7  HPFS/NTFS
/dev/sda6           13524       18745    41945683+  83  Linux
/dev/sda7           18746       19267     4192933+  82  Linux swap / Solaris

```

Partition Descriptions:
1: Media Partition between OS's
5: XP
6: Ubuntu
7: Swap (that is unnecessarily big? haha)
2: ??


Thanks a ton!
-Ryan Donnelly

---

### Post by rsambuca on 2007-12-11
I may be wrong, but I don't think XP can live in a logical partition.  I think you will have to install it to a primary partition.

---

### Post by RDonnelly on 2007-12-11
Are you talking in general, or with Ubuntu running?  I was running the XP partition fine earlier today.

Is there any way to move it?  Or will I have to go clean?

---

### Post by santaslittlehelper on 2007-12-11
Hi

Not sure at all, but -
If XP was ok before you installed ubuntu then GRUB might be trying to boot XP on /dev/sda1, I think the same happens in some cases when a "recovery partition" is placed on /dev/sda1 by default. 

If so you could post the output of -
```
cat /grub/boot/menu.lst
```

---

### Post by RDonnelly on 2007-12-11
```
## ## End Default Options ##

title Windows XP
root (hd0,4)
chainloader +1

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6e7b63e9-6c46-41ad-8d0e-7f70d12e1241 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6e7b63e9-6c46-41ad-8d0e-7f70d12e1241 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```


Thanks so much for the quick replies!
-Ryan Donnelly

---

### Post by santaslittlehelper on 2007-12-11
It looks fine to me, but that's not saying a lot. :(

This was what made most sense too me -
[http://wiki.wolvix.org/Partitioning](http://wiki.wolvix.org/Partitioning)

If that's the case I think you would have to change "root (hd0,4)" accordingly, ill leave that to you or someone else, if that's even what's needed.

ps
sorry about, /grub/boot thing :)

---

### Post by PeterJS on 2007-12-11
> **RDonnelly said:**
> 
Partition Descriptions:
1: Media Partition between OS's
5: XP
6: Ubuntu
7: Swap (that is unnecessarily big? haha)
2: ??


Partition #2 is the physical partition that contains the logical partitions (5-7).

---

### Post by mcduck on 2007-12-11
> **RDonnelly said:**
> ```
## ## End Default Options ##

title Windows XP
root (hd0,4)
chainloader +1

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6e7b63e9-6c46-41ad-8d0e-7f70d12e1241 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6e7b63e9-6c46-41ad-8d0e-7f70d12e1241 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```


Thanks so much for the quick replies!
-Ryan Donnelly

While not actually related to the problem, I just needed to point out that you should move your Windows entry to some other place in the menu.list file. Everything inside the AUTOMAGICurself from a lot of trK KERNEL LIST area will get erased when you get kernel updates, so you would loose the Windows entry..

Move it either above or below the AUTOMAGICK area and you'll save yourself from a  load of trouble. :)

Edit: You could try if one of these entries works for your Windows:

```
title Windows XP
rootnoverify (hd0,4)
makeactive
chainloader +1
```
This is similar to what I use to boot Windows.

```
title Windows XP
map (hd0,0) (hd0,4)
map (hd0,4) (hd0,0)
rootnoverify (hd0,0)
makeactive
chainloader +1
```
This one swaps the places of partitions while booting, making Windows believe that it's on the first partition. Windows has sometimes problems if it's not on the first partition of the first disk, so even when it worked for you before this mifgt be worth a try.

---

