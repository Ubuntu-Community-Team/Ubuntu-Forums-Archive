---
title: "EFI problems"
date: 2009-05-14
forum: Apple Hardware Users
---

### Post by mfleming on 2009-05-14
Folks, 

I'd really appreciate some help getting Linux to work on my new MBP. I installed Windows using Bootcamp, then Ubuntu 9.04 to partition /dev/sda3, instructing it put grub on /dev/sda3. Then I installed rEFIT. Now, rEFIT shows icons for, and can boot into, OS X and Vista, but does not show an icon for Linux.

The rEFIT partitioner shows partion 3 as "Basic Data" in the GPT partition table, and type 83 Linux in the MBR table. This seems OK. Also the partitioner says that the two tables are in sync. I had synced them originally.

I thought about running grub again to reinstall the bootloader to /dev/sda3, but was afraid to because I don't know what grub wants to call /dev/sda3. I've tried running off a CD, mounting /dev/sda3, and running grub> find /boot/grub/stage1, but for some reason grub> find can't seem to find anything; I keep getting "file not found" errors. Parted correctly labels /dev/sda3 as /dev/sda3, but /boot/grub/menu.1st has the Linux partition as (hd0,0). I have no idea why. 

Incidentally, /dev/sda3 is formatted as XFS.

Would really appreciate some help with this one.

Thanks,

Matthew Fleming

---

### Post by cyberdork33 on 2009-05-14
you can try to reinstall grub, but GRUB+XFS has been a bad idea for awhile. if you want to use XFS for your root partition, then you should separate your /boot partition and make it ext2 or ext3.

---

### Post by mfleming on 2009-05-14
Thank you. I reinstalled using ext3 and all is well.

---

