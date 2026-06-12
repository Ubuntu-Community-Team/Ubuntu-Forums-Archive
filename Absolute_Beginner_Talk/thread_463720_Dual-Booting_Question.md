---
title: "Dual-Booting Question"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by th3void on 2007-06-04
I've read the other posts about installing both Windows XP and Ubuntu using 2 IDE HDD's.  It seems that many of them recommend making the Linux drive the Primary Master and the Windows drive the Primary slave.  However, due to the layout of my motherboard and the length of cables I've got (yeah, this box is pretty ghetto) I essentially must have my Windows drive as Primary master and my Linux drive as Secondary Master.  I also have a third HDD for storage, which is Secondary slave.

Anyhow, if I unplug the Linux HDD, I can make Windows work just fine.  And, if I unplug the Windows HDD, I can make GRUB load Linux just fine.  However, now that everything is plugged in, I'm a bit confused on how to add an entry to my menu.lst for my Windows entry.  Here is what I've got now, for the Linux menu.lst entry:

```

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=10ccee18-2d2c-4e43-8554-f4ece6c6bf94 ro quiet splash
initrd          /initrd.img-2.6.20-16-generic
quiet
savedefault

```

This is all well and good.  I was going to add an entry for Windows, so I was looking at device.map to see how to reference my Windows drive (hd1,0 or whatever it should be) but this is what I get...

```

(hd0)   /dev/hdc

```

That is, no entry for the other HDD's anywhere.  Here is the output on sudo fdisk -l...

```

alex@ubuntu:/boot/grub$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5004    40194598+   7  HPFS/NTFS

Disk /dev/hdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         122      979933+  83  Linux
/dev/hdc2             123         365     1951897+   5  Extended
/dev/hdc3             366       38913   309636810   83  Linux
/dev/hdc5             123         365     1951866   82  Linux swap / Solaris

Disk /dev/hdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       38912   312560608+   7  HPFS/NTFS


```

hda is my Windows drive, hdc is my Linux drive, and hdd is my storage drive.  Where do I need to go from here to add an entry to menu.lst for Windows?

Thanks in advance!

---

### Post by th3void on 2007-06-04
Also, to be more specific, I have a general idea of how to add a menu.lst entry; however, I don't know if I need to add something to device.map (manually?  automatically?) so that my Windows drive gets assigned something like hd1,0 in device.map.

---

### Post by confused57 on 2007-06-04
You should be able to follow this guide, as far as editing your /boot/grub/menu.lst and the entry you'll need to boot Windows:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Added:  You shouldn't have to add anything to your device.map.

---

### Post by th3void on 2007-06-04
Right; I'm on that page right now.  However, for the entry for Windows, I have to reference /dev/hda somehow.  From what I can tell, it is usually of the form (hd1,0) or (hd0,0) or something like that.  I don't know what to put for that part for my Windows drive.  I thought device.map would tell me this, but it doesn't have any entry for my Windows HDD, so I don't know what to put...

---

### Post by th3void on 2007-06-04
To be more specific...  I will highlight the line I am having issue with.

```

title              Windows XP
root               (hd1,0)           **<-------  I don't know what to put here.**
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

```

---

### Post by confused57 on 2007-06-04
Try it exactly as it is...if it doesn't work, we'll go from there. e.g.

```
title              Windows XP
root               (hd2,0)          
savedefault
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader        +1
```

---

### Post by th3void on 2007-06-04
Alrighty.  Well, what I did do was add an entry

(hd1) /dev/hda1

entry to my device.map file.  Then I added the entry to menu.lst exactly as your original dual-boot tutorial had it listed, rebooted, and it all worked just fine.  Frankly I was afraid to do it all myself without some verification, because this system has blown up so much it isn't even funny anymore...  four Ubuntu re-installs today alone.  But we're all better now.

Thanks for your help!

---

### Post by Inxsible on 2007-06-04
your menu list entry would have to be (hd0,0)
 
and you wouldnt have to put anything in the device.map.
 
You windows is in the /dev/hda1...therefore its the first disk (a) and the first partition(1)
 
Maps are always zero-based. so therefore your entry would be (hd0,0)
 
That would be another way of looking at it. But since you already got it fixed ....well :)

---

### Post by th3void on 2007-06-04
> **Inxsible said:**
> your menu list entry would have to be (hd0,0)
 
and you wouldnt have to put anything in the device.map.
 
You windows is in the /dev/hda1...therefore its the first disk (a) and the first partition(1)
 
Maps are always zero-based. so therefore your entry would be (hd0,0)
 
That would be another way of looking at it. But since you already got it fixed ....well :)

Actually, I installed GRUB on my Linux drive, when it was the only one plugged in.  Also, during the Ubuntu install, I had hdc (my Linux drive) set as the first boot device, and my Windows drive was unplugged.  Perhaps this is why the device.map didn't originally have an entry for hda, and why hdc was listed as (hd0) ?

---

### Post by Inxsible on 2007-06-04
your solution works because you dont have a hdb i.e. a second drive. Therefore the hd1 is free and available for use. Therefore you mapped it to /dev/hda1 and thats why you could use hd1 as alias to hd0, which is why you have the map keys in your menu entry.
 
If you just put in (hd0,0) you dont need the map entries.

---

### Post by Inxsible on 2007-06-04
> **th3void said:**
> Actually, I installed GRUB on my Linux drive, when it was the only one plugged in. Also, during the Ubuntu install, I had hdc (my Linux drive) set as the first boot device, and my Windows drive was unplugged. Perhaps this is why the device.map didn't originally have an entry for hda, and why hdc was listed as (hd0) ?
 
yeah not having the other drives connected during install might have played a hand in the naming of the devices.

---

