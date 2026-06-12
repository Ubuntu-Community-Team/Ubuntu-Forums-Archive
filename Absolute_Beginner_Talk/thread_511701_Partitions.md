---
title: "Partitions"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by newtonrealman on 2007-07-28
Hello!
I have windows currently installed and i was excited to give ubuntu a try.
I then started ubuntu installation and when it asked about partition i set it up to 30%.
After the installation I realised that actually my windows has 30% and ubuntu has 70% but i wanted it the other way round. How can i fix this problem?
If i've got to remove the linux and install it again.. how do i remove it? Just by deleting the partition?
Thanks,
Newton

---

### Post by jingo811 on 2007-07-28
Yes deleting your linux partition is good.

---

### Post by az on 2007-07-28
> **newtonrealman said:**
> Hello!
I have windows currently installed and i was excited to give ubuntu a try.
I then started ubuntu installation and when it asked about partition i set it up to 30%.
After the installation I realised that actually my windows has 30% and ubuntu has 70% but i wanted it the other way round. How can i fix this problem?
If i've got to remove the linux and install it again.. how do i remove it? Just by deleting the partition?
Thanks,
Newton

I think it would be simpler for you to do the latter.  Boot the installer again, get to the partitioning stage and pick manul partitioning.  Then delete the Ubuntu partition.  The nake the windows partition bigger, but still keeping the desired amount of free space around.

The click go back.  At the partitioning step again, puck use free space...

You're done.

> **jingo811 said:**
> Yes deleting your linux partition is good.

In of itself, this will leave the computer unbootable, since grub will be on the partition you just deleted.  You would have to reinstall the windows bootloader so that you would be able to boot into windows.

---

