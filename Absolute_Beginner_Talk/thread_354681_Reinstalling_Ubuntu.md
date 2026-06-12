---
title: "Reinstalling Ubuntu"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Hitchhiker42 on 2007-02-06
Well, my CPU/motherboard shuffled off this mortal coil over the weekend, and I think I'm going to replace the processor with an AMD64 (single core). Can I install the 64-bit version of Ubuntu directly over the top of my current version, or do I need to uninstall the original first? Is there anything else that I need to keep in mind as I upgrade? (This is my first time doing anything of this nature). 

I have to say, that even though I've only had about three weeks experience with Ubuntu, I've been very happy with it so far. I have the feeling that I'll have fewer problems with it on this upgrade than I will with the copy of 98 residing on my primary HD.

---

### Post by Iarwain ben-adar on 2007-02-06
Hi there,
If i were you, i would not install the 64-bit version yet: there is no significant speed difference.
Plus, most programs are built for 32-bit (flash, etc), so it would be quite hard (never done it myself i must say) to install those on your 64-bit system.


Iarwain

---

### Post by taurus on 2007-02-06
Yes, you can install Ubuntu using the same partition.  Just remember to have the installer to format the partition first.

---

### Post by Brunellus on 2007-02-06
unless you are

* using the computer as a database server

or

* doing a lot of video/audio encoding

AMD64 might be more trouble than it's worth.  64-bit kernels give you access to gobs of RAM (over the 4GB limit for 32-bit kernels) and seem to help with certain encoding tasks, but mostly it's not worth it.

---

### Post by lamego on 2007-02-06
Make sure you use another partition for /home, this will make your futures upgrades/reinstalls easier.

---

### Post by jvc26 on 2007-02-06
I'd second the /home partition idea. If you want to install 64bit over the other one you can, but you format the partition in the process hence a separate /home makes it easier and faster.
Il

---

### Post by Hitchhiker42 on 2007-02-11
Thanks for all your help! I've decided to go with the 32-bit version, and a new /home partition, as per y'all's recommendations. 

However, the saga continues. Quite aside from my Windows woes,* I have a PCI to IDE adapter card for my optical drives, and it doesn't appear to let me boot from either of them. I hold out hope of finding a setting or a workaround to correct this, but in the meantime, I may have to resort to a boot floppy for Ubuntu. I hope to copy the XP install CD to my HD and install it from there. Is there any way to do something similar for Ubuntu?

This is what I get for trying to make my old hardware work with new stuff. In retrospect, it might have been easier to just buy a new computer.

*I'll have to lay my poor, hardworking copy of 98SE to rest, because the drivers for my mobo only work with 2000/XP. But did they mention this on the box or in the printed documentation at all? Of course not.

---

