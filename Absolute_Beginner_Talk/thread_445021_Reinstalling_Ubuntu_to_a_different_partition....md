---
title: "Reinstalling Ubuntu to a different partition..."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-15
And grub gave me a no boot error.  Using the LiveCD, can I go in and change what partition GRUB is trying to mount?  I assume that's the issue since all the files are there, but my Ubuntu partition changed from /dev/sda5 to /dev/sda7.

If so, how do I log onto my drive to edit /boot/grub/menu.list from the LiveCD since I am not logged into that drive?

Thanks!

---

### Post by Happy_Man on 2007-05-15
Ok... boot the LiveCD, open up a terminal and type:
```
sudo mount /dev/sda
```

and then change /boot/grub/menu.lst from there.

---

### Post by annda on 2007-05-15
an easy guide with lots of info on how to configure GRUB:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

EDIT: oh, i see you don't need to reinstall it, sorry, the guide will be information overload.

---

### Post by gohanssjn on 2007-05-15
> **Happy_Man said:**
> Ok... boot the LiveCD, open up a terminal and type:
```
sudo mount /dev/sda
```

and then change /boot/grub/menu.lst from there.

Ah, so once it is mounted I have write access?  Excellent....

---

### Post by Happy_Man on 2007-05-15
So long as it's ext3 or FAT32, yes.

---

### Post by gohanssjn on 2007-05-15
Perfect.  It is ext3.

Had to format last ngiht and decided Ubuntu was too good to lose, but it had to move.  Right now, my HD is a brick until I 0 it out.  A LOT of partition moving last night made the table a mess and even add/delete in GParted is broken now.  But all my data is there in undifined partions that show up whenever I try to use something else to create partitions.  Just needs a good fresh wipe.

Thanks!

---

