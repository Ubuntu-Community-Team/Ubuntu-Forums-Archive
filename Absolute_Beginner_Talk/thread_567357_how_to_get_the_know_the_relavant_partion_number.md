---
title: "how to get the know the relavant partion number"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by path_finder on 2007-10-04
Hi every one,

I installed my /boot directory in to a seperate partion. Now i cant find out my machine actualy boot from that partion or the directory in the /root drive.
I want to knw the method of geting to know the relavant partion number of each partion.
ex:
   hdo,3
  hd2,5



Thanks.

---

### Post by eljalill on 2007-10-04
You just check on the partition manager (e.g. gparted), at least if you know the size of your partitions and the file system.

Also with sudo sfdisk -l /dev/hda in the terminal you can see a partition table.

---

### Post by forestpixie on 2007-10-04
> Device Boot      Start         End      Blocks   Id  System
/dev/hda1   [COLOR="Red"]hd0,0[/COLOR]            1        1094     8787523+  83  Linux
/dev/hda2   [COLOR="Red"]hd0,1[/COLOR]         1095        9889    70645837+  83  Linux
/dev/hda3   [COLOR="Red"]hd0,2[/COLOR]         9890       10011      979965   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   [COLOR="Red"]hd1,0[/COLOR]            1         829     6658911   83  Linux
/dev/hdb2   [COLOR="Red"]hd1,1[/COLOR]          830        8358    60476692+  83  Linux
/dev/hdb3   [COLOR="Red"]hd1,2[/COLOR]         8359        9729    11012557+  83  Linux

this is my fdisk - I've put the hd numbers which relate to menu.lst in RED 
 I assume that's what you're trying to work out

---

### Post by mendingo84 on 2007-10-04
how exactly did you you get those "hdx,x" because on my "fdisk -l" they don't show off

---

### Post by forestpixie on 2007-10-04
I didn't get them - I put them in for the op so he (assumption :) ) could see relationship between partitions and how grub counts partitions, it's the count from 0 - caught me out even though I'd read it 

from the op's post I'm guessing that there's a boot problem after adding /boot - so then grub has a problem

---

