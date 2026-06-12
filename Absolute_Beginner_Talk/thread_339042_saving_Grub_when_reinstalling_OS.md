---
title: "saving Grub when reinstalling OS"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by SVWander on 2007-01-15
This boxes dual boots between XP and Ubuntu 6.10. I am getting ready to reinstall XP but I need to know how to save my grub setting. Ubuntu is installed on the slave disk so I imagine the MBR is on the primary disk which XP will wipe clean. How do I keep grub in the MBR?
tim

---

### Post by ajgreeny on 2007-01-15
You can't.  You will need to reinstall grub after installing windows.
Easiest way is:-


Boot into the ubuntu live CD
open a terminal and run :
*sudo grub*
This gets you to a simple grub command line.
Then:
*find /boot/grub/stage1*
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
*root (hd?,?)*
[like : *root (hdo,1)* ,probably]
then:
[I]setup (hd0)
[/I]This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
*quit*
Finally reboot, and hopefully you will now have a working grub bootloader.

Good luck.

---

### Post by louieb on 2007-01-15
Your grub setting are on the Linux drive in /boot/grub/menu.lst. They should be safe but you can alway make a copy of that file just in case. But as ajgreeny stated It will be necessary to Reinstall GRUB to the MBR. The reinstall link in my signature basically rehashes the stuff ajgreeny posted here.

---

### Post by SVWander on 2007-01-15
> **ajgreeny said:**
> You can't.  You will need to reinstall grub after installing windows.
Easiest way is:-


Boot into the ubuntu live CD
open a terminal and run :
*sudo grub*
This gets you to a simple grub command line.
Then:
*find /boot/grub/stage1*
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
*root (hd?,?)*
[like : *root (hdo,1)* ,probably]
then:
[I]setup (hd0)
[/I]This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
*quit*
Finally reboot, and hopefully you will now have a working grub bootloader.

Good luck.

Thank you! It worked flawlessly! I wish reinstalling XP was going as well as configuring the grub.
tim

---

### Post by ajgreeny on 2007-01-16
My pleasure!  Isn't (K)ubuntu wonderful?  It just shows, there's no need to be fearful of the command line.

---

### Post by kinematic on 2007-01-16
howto reinstall grub is probably the most asked question on this forum.....if you would have done a search for "reinstall grub" you'd have gotten all the info you need.
if a mod would make a really BIG sticky this question would never have to be asked again because this is just rediculous!

---

### Post by bodhi.zazen on 2007-01-16
I think this question is up there with questions on how to mount, how to set monitor resolution, and wireless to name a few.

Perhaps a FAQ with links or short how-to's or links ??

Of course, perhaps we should write one up and PM it to the mods for their review :p

---

