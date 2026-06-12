---
title: "Unable to boot Windows: Windows drive is intact &amp; grub has entry for it"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by satyajitg2 on 2008-04-03
Hi,
I have lost my windows and I am not able to boot it.
However I have the windows drive intact and the grub menu.lst file has entry for the same.

This is the details of the disk in my system:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9aa69aa6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4205    33776631    7  HPFS/NTFS
/dev/sda2            4206        7296    24828457+   5  Extended
/dev/sda5            4206        7047    22828302   83  Linux
/dev/sda6            7048        7296     2000061   82  Linux swap / Solaris


And this is the menu.lst entry:

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c92082f7-4524-4da3-a28b-e6fb5213d74d ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c92082f7-4524-4da3-a28b-e6fb5213d74d ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault

Thanks for help in advance

---

### Post by edm1 on 2008-04-03
what error do you get when trying to boot windows?

---

### Post by Daveg4otu on 2008-04-03
Get into the C Drive (assuming that's where you have Windows) and check the boot.ini file is present and correct.

Do you possess a Windows disk for your version + a legal Product ID.?

---

