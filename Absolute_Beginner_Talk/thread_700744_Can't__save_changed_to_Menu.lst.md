---
title: "Can't  save changed to Menu.lst"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Stone9 on 2008-02-18
Hi guys,

I'm trying to edit my menu.lst so I can see my Vista installation. However, when I put an entry in, it won't let me save it. Does any one know how I can add a Vista installation to my Menu.lst? The Vista installation was there (on the same HD) before I installed Ubuntu.

Thanks,

Stone9

---

### Post by Joeb454 on 2008-02-18
From a terminal, type ```
gksu gedit /boot/grub/menu.lst
```

Then enter your password - It won't show you've entered anything though...not sure if you know that already

Anything outside the /home folder requires admin privileges to edit :) A security feature :)

---

### Post by Stone9 on 2008-02-18
Thanks for the response! Do you know what entry I should put if I want it to list a windows installation?

---

### Post by nixeagle on 2008-02-18
Depending on what partition windows is on, I'll assume windows is on the first partition of your drive. (This would be /dev/hda1). You will need to add the following to menu.lst:

title=Windows XP
rootnoverify (hd0,3)
makeactive
chainloader +1I'm hoping this is helpful :)

---

### Post by Stone9 on 2008-02-18
I will give that a try! I'm actually not sure which one it is either. However, on my desktop, my Vista parition is named sda5, but this doesn't have anything to do with that right?

---

### Post by Joeb454 on 2008-02-18
Well could you post the output of ```
sudo fdisk -l
``` so we can find out exactly what partition XP is on :)

*NOTE* that is a lower case L :) and you will have to input your password :)

---

### Post by Joeb454 on 2008-02-18
Oh if your Vista partition is /dev/sda5 then add the following to menu.lst
```

title		Windows Vista/Longhorn (loader)
root		(hd0,4)
savedefault
makeactive
chainloader	+1

```

---

### Post by nixeagle on 2008-02-18
Mmm, yeah posting it would probably be best if you want folks to check over it. Sorry about that assumption that XP was on the first partition.

---

### Post by Stone9 on 2008-02-18
I think I'm almost there!

When I made the change to 4, then rebooted and selected the Vista option, it said the device wasn't found. Could it be something else? Should I try other partitions?

Thanks!!!

---

### Post by Joeb454 on 2008-02-18
If you post the output of ```
sudo fdisk -l
``` We can tell you exactly what the number should be. Note that if the other options say sd(0, 1) etc. change the Vista option to sd and not hd :)


That might not've made sense, if not, let me know ;) :lolflag:

---

### Post by Stone9 on 2008-02-18
Here ya go!!! Thanks!

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x65fbed6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        1350       32300   233986725    5  Extended
/dev/sda5            2710        9481    51196288+   7  HPFS/NTFS
/dev/sda6            9482       32300   172511608+   7  HPFS/NTFS
/dev/sda7            1417        2709     9767488+  83  Linux
/dev/sda8            1351        1416      489951   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2046 MB, 2046033920 bytes
63 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      199216      491461   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(199215, 34, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(491460, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       43188      538843   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(43187, 17, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(538842, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      478721      974376   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(478720, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(974375, 14, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1      931190  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(931189, 36, 30)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 1023 MB, 1023933952 bytes
124 heads, 62 sectors/track, 260 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          21       80293+   0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 2)
Partition 1 has different physical/logical endings:
     phys=(9, 254, 63) logical=(20, 111, 8)
Partition 1 does not end on cylinder boundary.
/dev/sdc2              21         261      919610+   b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(10, 0, 1) logical=(20, 111, 9)
Partition 2 has different physical/logical endings:
     phys=(124, 123, 62) logical=(260, 15, 61)

---

### Post by Stone9 on 2008-02-18
Sorry, didn't directly post this to the thread...

Here ya go!!! Thanks!

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x65fbed6e

Device Boot Start End Blocks Id System
/dev/sda2 * 1350 32300 233986725 5 Extended
/dev/sda5 2710 9481 51196288+ 7 HPFS/NTFS
/dev/sda6 9482 32300 172511608+ 7 HPFS/NTFS
/dev/sda7 1417 2709 9767488+ 83 Linux
/dev/sda8 1351 1416 489951 82 Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2046 MB, 2046033920 bytes
63 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot Start End Blocks Id System
/dev/sdb1 ? 199216 491461 570754815+ 72 Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
phys=(357, 116, 40) logical=(199215, 34, 11)
Partition 1 has different physical/logical endings:
phys=(357, 32, 45) logical=(491460, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2 ? 43188 538843 968014120 65 Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
phys=(288, 115, 43) logical=(43187, 17, 47)
Partition 2 has different physical/logical endings:
phys=(367, 114, 50) logical=(538842, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3 ? 478721 974376 968014096 79 Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
phys=(366, 32, 33) logical=(478720, 18, 30)
Partition 3 has different physical/logical endings:
phys=(357, 32, 43) logical=(974375, 14, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4 ? 1 931190 1818613248 d Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
phys=(0, 10, 0) logical=(931189, 36, 30)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 1023 MB, 1023933952 bytes
124 heads, 62 sectors/track, 260 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x20202020

Device Boot Start End Blocks Id System
/dev/sdc1 1 21 80293+ 0 Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
phys=(0, 1, 1) logical=(0, 1, 2)
Partition 1 has different physical/logical endings:
phys=(9, 254, 63) logical=(20, 111,
Partition 1 does not end on cylinder boundary.
/dev/sdc2 21 261 919610+ b W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
phys=(10, 0, 1) logical=(20, 111, 9)
Partition 2 has different physical/logical endings:
phys=(124, 123, 62) logical=(260, 15, 61)

---

### Post by stchman on 2008-02-18
> **Stone9 said:**
> Hi guys,

I'm trying to edit my menu.lst so I can see my Vista installation. However, when I put an entry in, it won't let me save it. Does any one know how I can add a Vista installation to my Menu.lst? The Vista installation was there (on the same HD) before I installed Ubuntu.

Thanks,

Stone9

If you installed Ubuntu after Vista then Vista will appear in the menu.lst file automatically.

---

### Post by Joeb454 on 2008-02-18
Ok so judging by your last post,you should either use ```

title		Windows Vista/Longhorn (loader)
root		(hd0,4)
savedefault
makeactive
chainloader	+1
```

OR

```

title		Windows Vista/Longhorn (loader)
root		(hd0,5)
savedefault
makeactive
chainloader	+1

```

Hope this helps :) *NOTE* if the above fails, then also try changing "hd" to "sd" and the 0 to a 1 :)

---

### Post by Stone9 on 2008-02-18
That's what I hear, but unfortuanately it didn't :(

---

### Post by Stone9 on 2008-02-18
I tried both but I keep getting

Error 12 : "unknown device request"

Should I try using the windows vista disc to renable the bootup?

Thanks!

Jason

---

