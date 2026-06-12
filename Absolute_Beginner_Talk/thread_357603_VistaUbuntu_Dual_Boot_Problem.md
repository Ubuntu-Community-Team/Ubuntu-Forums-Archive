---
title: "Vista/Ubuntu Dual Boot Problem"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by The55Gon on 2007-02-09
Okay so i installed ubuntu the other day, and that went fine. i had to repartition some my only harddrive to do so. prior to this, i had vista installed. 

i repartitioned my drives to the following... 

15gb to vista
15gb to root
512mb to swap
60gb to home

The problem is, that vista doesnt start anymore. at the grub loader, if i select vista, it just keeps loading indefinitely. 

does anyone have a clue as to why this happens?

---

### Post by AndyCooll on 2007-02-09
See the link in my signature for all dual-boot issues.

:cool:

---

### Post by confused57 on 2007-02-09
> **The55Gon said:**
> Okay so i installed ubuntu the other day, and that went fine. i had to repartition some my only harddrive to do so. prior to this, i had vista installed. 

i repartitioned my drives to the following... 

15gb to vista
15gb to root
512mb to swap
60gb to home

The problem is, that vista doesnt start anymore. at the grub loader, if i select vista, it just keeps loading indefinitely. 

does anyone have a clue as to why this happens?
Boot into Ubuntu, open a terminal(Applications--Accessories--Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"
this will show your partition table(s) as Ubuntu recognizes them

then, from the terminal:
```
gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list, not menu.first

just post the entries near the bottom of the file for booting Ubuntu & Vista

The link AndyCooll gave you for dual-booting is the best dualboot & bootloader grub I know of.

---

### Post by The55Gon on 2007-02-09
Thanks for your help guys, heres what it shows:

sudo fdisk -l

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/sda2            3982       11977    64227870    c  W95 FAT32 (LBA)
/dev/sda3            1959        3916    15727635   83  Linux
/dev/sda4            3917        3981      522112+  82  Linux swap / Solaris

Partition table entries are not in disk order

gedit /boot/grub/menu.lst

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by confused57 on 2007-02-09
Your Windows entry looks like it should boot, based on your fdisk -l output...what you can try is to change the line:
root  (hd0,0)

to

rootnoverify  (hd0,0)

sometimes this works, I'm not personally familiar with Vista, though.

You might want to download the Super Grub Disk(approx a 500 kb download) & burn to cd:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

How to edit your /boot/grub/menu.lst:

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

copy & paste each line one at a time, press enter between each line.
The first line changes to the /boot/grub directory
second line makes a backup copy of your menu.lst file
third line opens your menu.lst in the gedit text editor

Quit & save.

---

### Post by The55Gon on 2007-02-09
i just tried that and no success T_T

---

### Post by confused57 on 2007-02-10
> **The55Gon said:**
> i just tried that and no success T_T

You might want to try the Super Grub Disk, it can boot Windows(not sure about Vista) & Linux, as well as repair the mbr.

---

### Post by Coelocanth on 2007-02-10
You may be interested in [Click Here](http://www.pro-networks.org/forum/about78184.html). Apparently, you're not supposed to resize the Vista partition during the Linux install. Perhaps that's where your problem lies.

---

### Post by confused57 on 2007-02-10
> **Coelocanth said:**
> You may be interested in [Click Here](http://www.pro-networks.org/forum/about78184.html). Apparently, you're not supposed to resize the Vista partition during the Linux install. Perhaps that's where your problem lies.

Nice link...good to know.

---

### Post by The55Gon on 2007-02-10
alright, i solved the problem the hard way. i just reinstalled windows then reinstalled ubuntu -_-.
i didnt have anything valuable on those partitions so it worked out okay

---

