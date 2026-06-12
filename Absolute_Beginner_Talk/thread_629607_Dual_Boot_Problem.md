---
title: "Dual Boot Problem"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by masarwar1 on 2007-12-02
ok now the thing is installed ubuntu 7.1, and i have a windows vista ultimate on the other partition, when i tried booting into windows vista to copy my university's documents, it wont met me go in, instead it started up windows recovery. now after inspection of the menu.lst file, i saw that my windows mount was set to hda 0.1 , and my windows partition was hda 0.3. now i tried editing the menu.lst file to correct it, but it wont let me edit or save it. any way to solve this issue plz?

---

### Post by Jolly-Swagman on 2007-12-02
You will need to be root to edit the file,,
 Sudo gedit  /boot.conf

---

### Post by masarwar1 on 2007-12-02
thanks, i did try that, but when i restarted the whole thing, and went in there, it was giving me and error of unrecognizable format :(

is there any way to save it? i just need to copy those files and thats it.

---

### Post by cotcot on 2007-12-02
Can you please check the annotation for the partitions ?
I expect either (hd0,1) or  hda2 or sda2. 
Also helpful is posting the output of ```
sudo fdisk -l
``` and your file menu.lst.

---

### Post by masarwar1 on 2007-12-02
here it is mate:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52df0fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1             894        3447    20515005   83  Linux
/dev/hda2               1         893     7172991    b  W95 FAT32
/dev/hda3            3635       14593    88028167+   7  HPFS/NTFS
/dev/hda4   *        3448        3634     1502077+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Walter_Crankite on 2007-12-02
If you an absolute beginner, better follow some of the manuals.

[http://www.google.be/search?hl=nl&client=firefox-a&channel=s&rls=org.mozilla%3Aen-US%3Aofficial&hs=WtF&q=dual+boot+ubuntu+and+vista&btnG=Zoeken&meta=](http://www.google.be/search?hl=nl&client=firefox-a&channel=s&rls=org.mozilla%3Aen-US%3Aofficial&hs=WtF&q=dual+boot+ubuntu+and+vista&btnG=Zoeken&meta=)

---

### Post by masarwar1 on 2007-12-02
well i have used ubuntu before, and i have done a dual boot with windows XP.

this time i used the same steps that i did in windows XP for windows vista

---

### Post by cotcot on 2007-12-02
+1 for the previous post.
You followed a not recommended way. It is better to have windows on the first partition.
The link of the previous poster should help you. Or you could search on the forum here. Your problem is not unique.
Your files that you wanted to copy should be accessible from a liveCD.

---

### Post by masarwar1 on 2007-12-02
isnt there any way just to access the windows vista partition?

bcoz i remember even in live cd, i was getting the "recovery" drive.

---

### Post by meierfra on 2007-12-03
Try this:

Open menu.lst via

```
sudo gedit /boot/grub/menu.lst
```

And add this to the end of the file:

title  Vista
rootnoverify (hd0,2)
makeactive
chainloader +1

---

