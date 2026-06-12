---
title: "Hard Drive won't stop + boot problems"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-04-09
I've been dual booting XP &  Feisty for about 4 months without a problem on a Toshiba Laptop.
I was using Filezilla to upload some files to my web-site &  Feisty sort of locked up where the programs wouldn't open or close. Using ctrl-Alt-F1 I got to tty & did "sudo reboot". 
On booting into Feisty it starts to show boot status & the goes to tty & hangs on Swapfile..loading . or something like that.  If I ctrl-alt-del from there it gets me back into the GUI
& everything looks normal but my HD never stops running. It acts like its constantly searching for something. Every runs at a snails pace in Feisty but if I boot back into XP everything runs normal.
Any ideas?

---

### Post by Fate Reconciled on 2008-04-10
Run sudo fdisk -l

Post output here

---

### Post by garyed on 2008-04-10
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2117    17004771    7  HPFS/NTFS
/dev/sda2            2118        3577    11727450   83  Linux
/dev/sda3            3578        3648      570307+   5  Extended
/dev/sda5            3578        3648      570276   82  Linux swap / Solaris

After shutting down for a few hours everything started working O.K. but still every so often at boot up  the screen will lock up & I can't even ctrl-alt-f1 to get into tty.  I have to power down my laptop, Sometimes it boots up & rune fine & sometimes not. I wonder if my HD is going bad or my Swap drive ? Right now its woking fine.

---

