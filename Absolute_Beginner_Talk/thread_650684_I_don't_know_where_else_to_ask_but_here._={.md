---
title: "I don't know where else to ask but here. ={"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2007-12-26
Ok, so my main hdd is split in half i have windows vista on one half and linux ubuntu on the other half. but today i went out and bought an external hdd and now i'm trying to install backtrack to it and then i'll be try booting. but i don't see an opption to install it to the external? below is my options. maybe one of them is it and i just don't know it? (oh and just incase it makes a difference my external is a seagate free agent 120gb)

---

### Post by overdrank on 2007-12-26
> **RadiationHazard said:**
> Ok, so my main hdd is split in half i have windows vista on one half and linux ubuntu on the other half. but today i went out and bought an external hdd and now i'm trying to install backtrack to it and then i'll be try booting. but i don't see an opption to install it to the external? below is my options. maybe one of them is it and i just don't know it? (oh and just incase it makes a difference my external is a seagate free agent 120gb)

HI and it appears in the screen shot that there is 4 partitions and 2 drives.  Use this command ```
sudo fdisk -l
``` that is a lower case L 
 after looking at mine I would bet it is sdb1

---

### Post by RadiationHazard on 2007-12-26
This is what it did.
```
t ~ # sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         795     6379520   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         795       13446   101622784    7  HPFS/NTFS
/dev/sda3           13447       14538     8771490   83  Linux
/dev/sda4           14539       14593      441787+   5  Extended
/dev/sda5           14539       14593      441756   82  Linux swap

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS
```

---

### Post by overdrank on 2007-12-26
Ok here is the sure fire way to tell. Unmount the external drive then run the command again that will tell. :KS:)

---

### Post by RadiationHazard on 2007-12-26
```
bt ~ # sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         795     6379520   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         795       13446   101622784    7  HPFS/NTFS
/dev/sda3           13447       14538     8771490   83  Linux
/dev/sda4           14539       14593      441787+   5  Extended
/dev/sda5           14539       14593      441756   82  Linux swap
```

did that help you so you know what i'm supposed to do? =\

---

### Post by overdrank on 2007-12-26
> **RadiationHazard said:**
> ```
bt ~ # sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         795     6379520   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         795       13446   101622784    7  HPFS/NTFS
/dev/sda3           13447       14538     8771490   83  Linux
/dev/sda4           14539       14593      441787+   5  Extended
/dev/sda5           14539       14593      441756   82  Linux swap
```

did that help you so you know what i'm supposed to do? =\

You mean did it help you. As you can see for the difference in the out put of that command that the external drive is 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS
If you indeed unmounted the drive. :KS

---

### Post by RadiationHazard on 2007-12-26
so all i do is install it to that drive...correct?
:KS

---

### Post by overdrank on 2007-12-26
> **RadiationHazard said:**
> so all i do is install it to that drive...correct?
:KS

Well it is your data and your risk. I was just trying to help you locate the drive. :KS

---

### Post by RadiationHazard on 2007-12-26
haha. alright well when i plugged the drive back in something different popped up when i just ran that command. screen shot below

---

### Post by overdrank on 2007-12-26
> **RadiationHazard said:**
> haha. alright well when i plugged the drive back in something different popped up when i just ran that command. screen shot below

Ok, it is mounted as sdc1 now. The point being is it is the drive other than sda.

---

### Post by RadiationHazard on 2007-12-26
haha. alright. i'll try it and let you know what happens. wish me luck!!

---

### Post by overdrank on 2007-12-26
> **RadiationHazard said:**
> haha. alright. i'll try it and let you know what happens. wish me luck!!

Best of luck!:KS

---

