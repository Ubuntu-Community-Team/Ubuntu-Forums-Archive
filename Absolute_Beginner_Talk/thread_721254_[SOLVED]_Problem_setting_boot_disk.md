---
title: "[SOLVED] Problem setting boot disk"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by notbitmonk on 2008-03-11
This is the output of my fdisk:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa814c459

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9733    78180291   83  Linux

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd011d011

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         608     4883728+  82  Linux swap / Solaris
/dev/sda2             609       14593   112334512+  83  Linux

I installed Kubuntu and my main disk is sda not hda.  hda is where I store my data.  How can I make sda my boot disk?

---

### Post by jken146 on 2008-03-11
You probably don't want to do that, as the master boot record will most likely be on hda, as it is the first disk that the BIOS recognises.  If you change your BIOS settings so that sda is booted instead of hda, you'll find that there is no bootloader to be found and you'll have to reinstall GRUB.  That will be some hassle and I don't see any benefit.

---

### Post by notbitmonk on 2008-03-11
Even when the bios is set to start with the sda disk?  I have installed and reinstalled multiple time.  sda is a SATA disk and every time i have installed, there is always trouble with grub error 22 (I have been able to fix it though).  I think that the error happens because the boot record is in hda and when it loads, is looking for the wrong disk.

---

### Post by jken146 on 2008-03-11
You can choose where GRUB is installed to in the Ubuntu installer.  Post the output of ```
cat /boot/grub/menu.lst
``` if you like, and we'll see where it's looking.

---

### Post by notbitmonk on 2008-03-12
Actually I did what you said on a previous post.  My SATA disk was set as my first boot disk in the BIOS and every installation I had made was troublesome.  I had changed it  because when I had MS Windows, I ran into some trouble and was able to fix it by setting the SDA disk as the first disk.  In the couple days since, I have (re)installed Kubuntu like five times just to make sure that that was my problem and you're right.  Now I know not to mess with the boot disk order.  Of the five times I (re)installed Kubuntu, the hda disk didn't had write permissions twice and I had to edit fstab.  Otherwise, things have gone smooth.  Righ now, I'm downloading the updates.  Anyways, thank for your advise.

---

