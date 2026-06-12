---
title: "[SOLVED] Grub error 17"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-10-27
I have a dual boot xp and ubuntu 7.04 on the master drive.  I then tried installing gutsy on to a slave drive. The install stopped at 82%. Ever since, I have had the problem of getting  the grub error 17. I tried  super grub disk, but this does not save the settings - I can boot into either xp or feisty via super grub disk, but the 'changes' are not saved. I have to use super grub disk every boot.
I have done a fdisk -l with the output below

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11090    89080393+   7  HPFS/NTFS
/dev/hda2           11091       11214      996030   82  Linux swap / Solaris
/dev/hda4           11215       15299    32812762+   5  Extended
/dev/hda5   *       11215       15299    32812731   83  Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         182     1461883+  82  Linux swap / Solaris
/dev/hdb2             183        6588    51456195   83  Linux

Disk /dev/sda: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         126     1007584+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 51)

Can anyone tell me what code I need to put into terminal to fix the problem.

At this stage I don't think I will try gutsy again, as up until then, everything was running fine. In fact, a friend of mine has given up on gutsy too. He has been unable to install either the 32 or 64 bit versions. There seems to be a problem with gutsy. I downloaded it twice (one torrent site, the other through internode), both stop at 82% when installing. Is this a known problem? I was really looking forward to gutsy, so far it has been a major disappointment.

---

### Post by Bliepo32 on 2007-10-27
I think you need this: [How to restore Grub from a live Ubuntu cd.]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Pumalite on 2007-10-27
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by bumanie on 2007-10-27
Thanks bliepo32. Grub seems to be fixed.
However but does anyone know why gutsy would stop at 82% when installing? 
I thought when it happened from the first disc, it probably missed a torrent file or something, but when the same thing happened from the second disc, I can't help but think it something to do with the gutsy code.

---

### Post by Bliepo32 on 2007-10-27
Do you happen to have a computer with little RAM, and does it hang whilst configuring Anthy?

---

