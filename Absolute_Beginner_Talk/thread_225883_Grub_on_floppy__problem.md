---
title: "Grub on floppy  problem"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Gambylad on 2006-07-30
I have installed using the alternate cd and when asked I installed grub to (fd0) but when I reboot at end of installation boots to black screen and word grub followed by flashing cursor but goes no further

Windows on 1st sata disk ubuntu on second ide disk

any help would be appreciated

---

### Post by catlett on 2006-07-30
If you know the partition ubuntu is on, you can manually enter the grub lines. For example if ubuntu is on the first partition of your second ide drive you can try this
```
grub>rootnoverify (hd1,0)
```
```
grub>chainloader +1
```
```
grub>boot
```If that works you can install grub to a floppy again but it will be a little involved, I am assuming you do not want grub on the mbr of the first drive?
To put grub on  floppy, you first have to put grub on it's own partition. This will keep grun off the mbr but you will need a floppy or another bootloader to start the boot process.Anyways if you get in, this will put grub on the ubuntu partition (assuming ubuntu is on /dev/hdb1) ```

sudo grub-install /dev/hdb1
```
Next you have to put it on a floppy. If all that worked, then follow these steps to put it on another floppy [http://www.ubuntuforums.org/showthread.php?t=224345](http://www.ubuntuforums.org/showthread.php?t=224345)

The biggest issue here is which partitiuon ubuntu is installed on.

---

