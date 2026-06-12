---
title: "ok dueal boot with two harddrives..."
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by sirlanceem on 2008-02-19
ok i ran the  sudo fdisk -l command and got this... 



Disk /dev/hda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65647b73

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2388    19181578+  83  Linux
/dev/hda2            2389        2498      883575    5  Extended
/dev/hda5            2389        2498      883543+  82  Linux swap / Solaris

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37243724

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS




i wanna know how i can dual boot to the serial ata drive that has windows xp on it... much thanks 

~sirlanceem~:lolflag:

---

### Post by dcstar on 2008-02-19
> **sirlanceem said:**
> ok i ran the  sudo fdisk -l command and got this... 



Disk /dev/hda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65647b73

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2388    19181578+  83  Linux
/dev/hda2            2389        2498      883575    5  Extended
/dev/hda5            2389        2498      883543+  82  Linux swap / Solaris

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37243724

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS




i wanna know how i can dual boot to the serial ata drive that has windows xp on it... much thanks 

~sirlanceem~:lolflag:

Try adding this to the end of you boot.lst file.

```
sudo gedit /boot/grubmenu.lst
```

```
title		Microsoft Windows XP
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

---

