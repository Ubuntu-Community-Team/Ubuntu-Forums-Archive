---
title: "Grub Error 17"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Dragonlaw on 2008-04-14
I used Testdisk to try and get back my windows partition. But when I clicked on the parition in testdisk and rebooted as instructed, I got this 

Grub loading 1.5
Grub Error 17. 

What do I do?

---

### Post by Dragonlaw on 2008-04-14
When I type /boot/grub/menu.1st file into the terminal (I've booted up thru LiveCD), it says that there is NO such file or directory.

After typing sudo disk -l I get

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectos/track, 10011 cylinders
Units = cyliders of 16065 * 512 = 8225280 bytes
Disk identifier:0x04260425

Device Boot    Start     End       Blocks      Id    System
/dev/sda1      9931     10011   650632+  f      W95 Ext'd (LBA)
/dev/sda5      9931     10011   650601    82    Linux swap / Solaris

Could anyone help? I'm using my sister's laptop and I don't think I can use it for long.

I already tried using Super Grub on a DVD but my desktop is unable to run it.

---

### Post by Pnut on 2008-04-14
> **Dragonlaw said:**
> I used Testdisk to try and get back my windows partition. But when I clicked on the parition in testdisk and rebooted as instructed, I got this 

Grub loading 1.5
Grub Error 17. 

What do I do?


The easiest way to recover from this is to overwrite your MBR using the windows cd, I would advise that you boot from a live cd first in order to back up your information on the linux partition before doing this.  this method hoses your linux install but you can get winders to boot normally and then re install linux on top of it.

" boot from windows cd like your going to re install windows, but utilize the recovery mode with command prompt.  Then use the FIXMBR command to repair your windows MBR.  This should get winders to boot normally.

Pnut

---

### Post by marquee moon on 2008-04-14
Alternatively, you can use "Super Grub Disk" to reconfigure you MBR.
It has an option for a guided (with help) configuration, and can find windows & linux OS's to produce a GRUB screen offereing both windows and ubuntu.

---

### Post by Dragonlaw on 2008-04-14
I'm sorry I don't have windows liveCD. And I was running testdisk to get back the windows partition but after I attempted to do so and rebooted the computer I cannot go in now. 

I tried Super Grub Disk. It doesn't work because I think I might have over written the Linux OS partition.

---

### Post by dstew on 2008-04-14
> I tried Super Grub Disk. It doesn't work because I think I might have over written the Linux OS partition.From your fdisk output it looks like you have deleted your Linux OS partition. The only partition left is a swap partition. The Windows partiton is also gone. You may have made a mistake using Testdisk in your recovery efforts. But, you still might be able to recover the partitions using Testdisk. Just be careful with it, and read the instructions.

---

### Post by Nick8692 on 2008-04-14
try this, it might work
[http://ubuntuforums.org/showthread.php?t=442945&highlight=grub](http://ubuntuforums.org/showthread.php?t=442945&highlight=grub)

---

