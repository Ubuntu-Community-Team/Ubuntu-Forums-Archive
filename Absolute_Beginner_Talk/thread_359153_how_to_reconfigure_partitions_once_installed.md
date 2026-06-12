---
title: "how to reconfigure partitions once installed"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by gtratter on 2007-02-11
I recently installed Ubuntu Dapper, quickly upgraded to Edgy and love it!.
When I first installed, I only set a very small portion of my laptop's HD aside and installed Ubuntu without a swap space (probably reading through things too quickly)
Here is what it looks like:

> 
gt@gt-laptop:~$ sudo fdisk -l

Disk /dev/sda: 78.7 GB, 78732380160 bytes
255 heads, 63 sectors/track, 9572 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        7435    59681475    7  HPFS/NTFS
/dev/sda3            8966        9571     4867695   db  CP/M / CTOS / ...
/dev/sda4            7436        8965    12289725   83  Linux



How would I go best about accomplishing 2 things:

1. give myslef a swap partition which Edgy will recognize without having to reinstall and

2. taking another 30 gig of sda2, making it into a ext2 or ext3 and mount it as workspace.

I am not 100% ready to give up the Windows installation, since it holds my BF1942 game - if not for that - I would wipe it clean.

I did a search on this forum and although I came up with many hits I am two nervous to go to the next step without a bit more specific advise. I do have **gparted** installed. 
Thanks for your help.

---

### Post by e_james on 2007-02-11
I notice that you have no replies as yet (except this one). Reading between the lines I suspect that we are about the same level of understanding of linux / ubuntu but I may be able to make some useful comments. 

1. There is a wiki guide to partitioning for ubuntu install which doesn't address your specific question but there may be helpful tips. Have you seen it?

2. I have seen some comments which suggest that resizing an NTFS partition (using Linux software) might be a bit iffy.

3. In my limited experience, if you can unmount a partition you can edit it and linux will recognise the change when it is remounted. In the case of a swap partition I would think you would need a restart. If mounting proves to be a problem, you can use a live CD.

---

### Post by gtratter on 2007-02-12
Thank you - I will start there....

---

### Post by Cardmaster91 on 2007-02-12
you could also try [gparted]("http://gparted.sourceforge.net/"), which is a unix like partition editor. Simply write it to cd, pop it in computer and restart. it has a very simple gui and is nice and easy to work with.

---

