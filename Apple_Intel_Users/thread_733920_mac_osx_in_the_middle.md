---
title: "mac osx in the middle"
date: 2008-03-24
forum: Apple Intel Users
---

### Post by Hotchilli on 2008-03-24
here is my disk layout

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa383a383

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         591     4747176    b  W95 FAT32
/dev/sda2           18826       19457     5076540   83  Linux

there is 139.68GB of unallocated space between sda1 and sda2 this is where some of the OSX install will go
I have refit on a cd as an iso 

now if i format some of the 139.68 to extended journal then install OSX how will this effect the boot loader  as at the moment GRUB is the boot loader?

hotchilli

---

### Post by afterkelsen on 2008-03-24
I suspect that you currently have GRUB installed on the master boot record of the disk?

If so, when you install OS X and refit, you will probably see all three OSes available in the refit menu but when you choose Windows or Linux then GRUB will appear. Or maybe only one of either Windows or Linux in refit will work. I am not entirely sure. I myself however dislike to have go through two boot managers on boot.

I have explained my setup [here]("http://www.twilightzone.dk/index.php/2008/03/22/ubuntu-and-windows-vista-dual-boot-on-a-macbook/"). A Vista - Ubuntu dual boot.

The idea is two leave the Windows boot manager alone, install GRUB on the Linux partition, and let refit function as the "real" boot manager. The GRUB boot manager can then be configured not to wait X seconds before booting the default linux kernel.

---

