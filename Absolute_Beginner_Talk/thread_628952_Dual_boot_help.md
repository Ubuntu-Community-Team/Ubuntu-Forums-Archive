---
title: "Dual boot help"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by khgiese on 2007-12-01
I am a ubuntu newbie and trying to figure out a dual boot issue.
I have Ubuntu install on sdb3 partition with the bootloader on sdb3 as well. 
Where I am having the problem is figure out how to do the following so the ubuntu.bin file is placed on my Ipod.

dd if-/dev/sdb3 of=/mnt/????/ubuntu.bin bs=512 count=1

How do i find out what my Ipod hard drive storage area is called?
Thanks in advance for any assistance offered.

KHGiese

---

### Post by khgiese on 2007-12-01
bump

---

### Post by khgiese on 2007-12-01
LOL sometimes it pays to just experiment.
I figured out how to place the file on one of my other partitions.
from the Ubuntu live cd terminal I simply did the following.

dd if=/dev/sdb3 of=/media/Games/ubuntu.bin bs=512 count=1

It worked.

KHGiese

---

