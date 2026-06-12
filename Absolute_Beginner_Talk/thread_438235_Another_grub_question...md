---
title: "Another grub question.."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by l0c0m0c0 on 2007-05-09
Hey guys I have been searching but cannot find an answer to my particular problem.  I have XP installed on a Raid0 setup and I have ubuntu installed on the 2ndary IDE channel.  Grub was installed as normal while installing ubuntu.  I do not get a grub menu unless I unplug my raid drives and have only the Ubuntu drive plugged in.  So I guess my question is, how do I get grub installed on my Raid drives MBR?

Ok, I just switched my IDE to be the main boot HD duh!  haha, ok but now I need to put XP on my raid setup in the grub menu..

Anyone know how to add a Raid0 to the grub boot menu?  I can't seem to get it right.

---

### Post by intel on 2007-05-10
h/w raid or s/w raid ?

---

### Post by l0c0m0c0 on 2007-05-10
Here is the code that works:

> title XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

I did have BOOT at the end but when I removed that it worked.

---

