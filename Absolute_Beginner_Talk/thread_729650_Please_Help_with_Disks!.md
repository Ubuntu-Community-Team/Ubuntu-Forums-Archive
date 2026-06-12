---
title: "Please Help with Disks!"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Timredd on 2008-03-20
Hi Guys:)

I'm yet another Linux newbie!
 also a computer newbie to be honest,
Anyway,

 I got a machine with 2 drives

One has XP

The other has Vista and Ubuntu 7.10 (with compiz fusion of course!)
 
It all works great

Windows Boot manager controls it all okay,  and when I wanna boot Linux it points to GRUB, no probs.

I want to create a swap/ page file on a new partition for Vista,

but,  after the last time I messed with the partitions GRUB couldn't find any OS (error 21, 22, 17 also I wasnt using windows boot manager when this happened) so  I had to reinstall Ubuntu and delete the extra partition

So, what do I do? please help :confused: :)

Ps not sure how to put an image on this post , so I've included an attachment of a screen shot of my Disk drive setup :)

---

### Post by Diabolis on 2008-03-20
Those grub errors are pretty common and easy to fix. Next time don't reinstall ubuntu, just reinstall  grub (the boot loader).

[grub page, might be hard to read]("http://users.bigpond.net.au/hermanzone/p15.htm")

[An example of how to do it]("http://ubuntuforums.org/showthread.php?t=725689")

The commands:
```
sudo grub
find /boot/grub/stage1          *It will find all the places **from where** you can install grub.*
root (hd?,?)                    *Select **from where** you want to install grub.*
setup (hd?)                     *Select the drive **in which** you want to reinstall grub.*
quit
```

---

### Post by bumanie on 2008-03-20
If you are triple booting, grub might work, but you will have better luck with easybcd bootloader. This may help 
[http://www.scotthofer.com/How%20to%20triple%20boot%20XP%20Vista%20Linux.html](http://www.scotthofer.com/How%20to%20triple%20boot%20XP%20Vista%20Linux.html)

---

### Post by Timredd on 2008-03-20
Thanks 4 The help guys!    :):)

---

