---
title: "Auto detect"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by zerek on 2007-10-23
Hi, 

I'm pretty new at Linux, just jumped away from windows, so yeah, I'm a n00bie.

anyhow, what my "current problem" is that i cant find a way to make Ubuntu 7.10 auto mount new USB devices. (like my usb portable hard drive, or logitech G7 mouse).

figured usb mouse will -auto install if i restart Ubuntu, but be kinda nice to auto detect it in some kinda  way.. 


but its the USB mem stick which is my problem.. 
I got the right settings on -Removable Drivers and Media Preferences, and USB stick is NTFS

when i type:
```
sudo fdisk -l
```

i only get this info,, not anything about my memory stick.. 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37793778

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10932    87811258+   7  HPFS/NTFS
/dev/sda2           10933       11952     8193150   83  Linux
/dev/sda3           11953       12161     1678792+  82  Linux swap / Solaris


Please help me,, And explain good if you can, I don't understand to much yet.

---

### Post by Martje_001 on 2007-10-24
Can you see your usb device in Locations --> Computer? Double click on it.

---

### Post by zerek on 2007-10-24
no, sorry. 
cant see usb drive there ether

---

