---
title: "[SOLVED] Ubuntu wont let me enable NTFS-3G..."
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by opheliax on 2008-02-12
Im trying to fix grub at the moment so that I can boot windows vista from it, I few very helpful people told me to dl and install NTFS-3G, unfortunately I cant add the option of enabling grub to be able to write to the driver, so I was wondering if there was a work around or something.

---

### Post by mikewhatever on 2008-02-12
> **opheliax said:**
> Im trying to fix grub at the moment so that I can boot windows vista from it, I few very helpful people told me to dl and install NTFS-3G, unfortunately I cant add the option of enabling grub to be able to write to the driver, so I was wondering if there was a work around or something.

NTFS-3g in pre-installed in Gutsy, verify it in Synaptic to be sure. As to grub writing to the ?drive/r?, what's up with that? Grub is just a boot manager, it usually does not 'live' on ntfs partition, so you should not need ntfs-3g driver at all.
Why don't you specify what's the problem with booting Vista, and post the outputs of the following:
sudo fdisk -l
cat /boot/grub/device.map
cat /boot/grub/menu.lst

---

### Post by HappyFeet on 2008-02-12
ntfs-3g has nothing to do with grub. read/write support for ntfs is enabled by default in gutsy. if you need to fix grub, see this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by opheliax on 2008-02-12
Reads as followed:
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5a2e3f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10891    87479217    7  HPFS/NTFS
/dev/sda2           10892       14561    29479275   83  Linux
/dev/sda4           14562       14593      257040   88  Linux plaintext


(hd0)   /dev/sda


-bash: syntax error near unexpected token `/dev/sda'


---

### Post by mikewhatever on 2008-02-12
Well, are you going to post the rest of it?

---

### Post by kaiju on 2008-02-12
yup, you still need to post your grub menu
```
cat /boot/grub/menu.lst
```
(its in there that you specify what and how to boot. and grub has nothing whatsoever to do with writing to ntfs, it just boots your os according to the entries in menu.lst.)

---

### Post by opheliax on 2008-02-12
That was all of it and its fine i figured it out, My vista partition got erased, dont know why though i did everything every tutorial said to do, probably a mcrosoft os getting butt hurt issue. but thanks alot for your guys help

---

### Post by jan quark on 2008-02-12
please mark this thread as solved when it is solved for you

thank you

---

### Post by kaiju on 2008-02-12
just a note in that case:
please make sure not to use the default partitioning when you install ubuntu, as that will (as it clearly tells you it will) erase all existing partitions on your hard drive.

---

### Post by opheliax on 2008-02-12
And I didnt do that, I went through manual so I screwed up somewhere else

---

