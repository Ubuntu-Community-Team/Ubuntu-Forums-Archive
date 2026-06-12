---
title: "Dual-boot system issues"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by dvryan on 2007-10-11
I have my hard drive partitioned and XP installed on one, Ubuntu on the other.  Right now, the 'boot' flag is set for XP, so when I start my computer it automatically starts XP.  I want to have the choice of OS each time I boot- ie get to choose either XP or Ubuntu each time I boot the machine. How do I get this to work?  I've tried removing the boot flag from XP but that didn't work.

---

### Post by celticbhoy on 2007-10-11
Dont know what you mean by set boot flag. Can you say whether you installed windows or Ubuntu first? Do you boot through 'Grub'?

---

### Post by dvryan on 2007-10-11
I installed ubuntu, then windows.  I don't know if I boot through grub. . . I assume I do.  I just know that, when I use gpartition, it shows the two systems, and has the boot flag set for the XP partition.  When I remove that boot flag, and reboot the system, it comes up and says 'insert boot disk to continue'.  So, I tried to set boot flags on both xp and ubuntu- no dice- only one can be set to boot.

---

### Post by celticbhoy on 2007-10-11
To begin with you have done this the hard way. If you had installed Ubuntu after windows, grub would install and automatically setup for both o/s's.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

use the above link to install grub, then

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

use this if you need help setting up grub.

---

### Post by dvryan on 2007-10-11
Thanks for the tip- I ran the commands you pointed me too, and now grub starts, but automatically kicks me into Ubuntu, rather than giving me the choice of OS.  Should I just uninstall Ubuntu and the swap, then re-install?

---

### Post by maybeway36 on 2007-10-11
Does it say that grub is starting?

---

### Post by dvryan on 2007-10-11
yes

---

### Post by twiceasworn on 2007-10-11
When grub is starting press the ESC key to have it pause, then you can pick which one to boot.  though I am sure there is a way to make it stop automatically on boot, but since it did it for me when I installed ubuntu I wouldn't know how to do that.

---

### Post by celticbhoy on 2007-10-11
open a terminal
type :-
#cd /boot/grub
#sudo gedit menu.lst

when the editoe opens look for the section that says timeout. will look like this

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

now check the setting beside the timeout command (30 in above example), and make sure the it is set to a reasonable number of seconds. then post back any results.

---

