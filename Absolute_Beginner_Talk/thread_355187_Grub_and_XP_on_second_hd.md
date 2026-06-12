---
title: "Grub and XP on second hd"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Phils on 2007-02-06
I have loaded winxp on a second hard drive, when I boot to windows as my secondary boot, grub hangs with the following:

Booting 'windows xp'
root (hd1,0)
filesystem type unknown,partition type 0x7
makeactive
chainloader +1

my entry in the menu.1st file is as following:

### END DEBIAN AUTOMAGIC KERNELS LIST


title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1


when I fdisk I get this:
phil@phil-desktop:~$ sudo fdisk map -lu  /dev/hdb
Password:

Disk /dev/hdb: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders, total 60030432 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    14329979     7164958+   7  HPFS/NTFS
/dev/hdb2        14329980    60018839    22844430   83  Linux
phil@phil-desktop:~$ 


when I use my super grub cd and use the choice "boot windows from second hard drive it boots right up into xp. So there can't be much really wrong, I just am not seeing what I have wrong in grub.
Any help will be greatly appreciated.
Thanks,
Phil

---

### Post by Phils on 2007-02-07
I just noticed that for whatever reason the windows install on the second hard drive starts at sector 63, could this be my problem?

---

### Post by confused57 on 2007-02-07
Try adding  some mapping lines to your Windows entry in grub:

title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


Note: there's a space between map<space>(hd0)<space>(hd1) & the other map line.
Taken from this guide:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by Phils on 2007-02-07
Thanks for the help):P  Works like a charm. If it weren't for one pesky CAD app I wouldn't even need the micro$oft partition.:lolflag:

---

