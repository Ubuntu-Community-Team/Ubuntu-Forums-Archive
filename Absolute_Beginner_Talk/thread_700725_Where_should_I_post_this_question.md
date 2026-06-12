---
title: "Where should I post this question?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Rashid01 on 2008-02-18
I need to install Ubuntu on a computer with an XP and Vista partition.  Vista was the later installation and controls the boot menu. 
I need to make the XP partition the default and have Ubuntu as an option.  Can I do this with the installation of Ubuntu in th free space? 

Where in the Forum can I post this question?  

Thank you very much in advance.
Rashid

---

### Post by Joeb454 on 2008-02-18
Yes you can, if you install Ubuntu into the free space, and use GRUB as the bootloader, we can help you configure it so that Ubuntu is an option in the Menu, and make XP the default system :)

This forum will be fine. If not the Mod's will move it when necessary

---

### Post by The Cog on 2008-02-18
This is the right place.

I suggest that you use the gparted partition editor in the live CD to delete the Vista partition. Then run the Ubuntu installer and tell it to install in to the free disk space. Beware, the default is to erase the entire disk. Installing in the free space cleared by deleting the Vista partition will create the partitions that Ubuntu needs. After install, the default boot will be Ubuntu with XP as an option. You can change the default later.

Back up all your valuable data first of course.

Edit - that's assuming you want to get rid of viata - maybe I misunderstood.

---

### Post by Forrest Gumpp on 2008-02-18
You are posting in the right place Rashid.  Perhaps your question could have been put a little more clearly as relating to triple-booting XP, Vista, and Ubuntu.

An excellent reference is Herman's Illustrated Dual Boot Site  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)  and within that site the page dealing with the GRUB bootloader.  See:  [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

