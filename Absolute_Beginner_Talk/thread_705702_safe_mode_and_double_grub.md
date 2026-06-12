---
title: "safe mode and double grub?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by crabclaw on 2008-02-23
I have no idea what's going on. First of all my computer keeps booting into safe mode in Ubuntu and I don't know how to make it stop or what happened to make it start doing so in the first place. For some reason it is also heating up way more than it ever has done. Second of all when Grub loads it shows two sets of ubuntu, one is 22.something and the other is 20 something else. So that's four lines in total in Grub plus memtest plus the alternative windows. 

Please help as I have loads of schoolwork to do and am severely Ubuntly Challenged and easily distracted by malfunctioning computers.

---

### Post by logos34 on 2008-02-23
Something happened to change the defaults.  (Update?)  Hit ESC key when you see the grub menu screen to stop the boot process.  Select 2.6.22-14 kernel.  

Then go into menu.lst and edit the preferences:

gksudo gedit /boot/grub/menu.lst

If the -22-14 kernel is first in the 'automagic' section, then the 'default' line near the top should be '**0**'.  You can also comment out (#) the previous -20 kernel.

Post your menu.lst if you want.

---

### Post by crabclaw on 2008-02-23
thank'ee kindly

---

