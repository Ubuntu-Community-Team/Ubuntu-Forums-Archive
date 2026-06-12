---
title: "Trouble Booting"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by YodaMstr on 2007-12-04
Alright, so, I got a new laptop recently from Dell.  I killed the 10 gig recovery partition and placed Ubuntu on there.  Everything went smoothly, and the install went off without a hitch.  The thing was, previous to this, on an older laptop, I had had a problem with the bootloader failing the installation and requiring me to fumble around with Vista.  So this time around I didn't install the bootloader.  It's installed and Vista starts up just fine, but I have no clue how to choose between Vista and Ubuntu or make it start up in place of Vista.  Any help?

---

### Post by marpstar on 2007-12-04
You'll have to install the bootloader... otherwise you have know way of choosing Vista or Ubuntu unless you configure the Vista bootloader to do so, which is no easy task.  I've had very good luck having GRUB installed on a Ubuntu/Windows dual boot situation, so don't let one experience prevent you from trying it again...

---

### Post by YodaMstr on 2007-12-04
How would I go about installing GRUB, then?  Will I have to reinstall Ubuntu in its entirety?

And it wasn't one failed experience.  Apparently the disk was flawed, and it would stop at ~56% of the installation.  I'm definitely not technically savvy, but I suppose it was just enough time to kill the Vista Bootloader.  So I didn't have GRUB or Vista's bootloader, and basically had to reformat Vista.  Seeing as how I had no clue how to get either bootloader up and working, that was my only choice. :p

---

### Post by marpstar on 2007-12-04
the easiest way to fix things would be to, yes, reinstall ubuntu from disc and allow it to install the bootloader...

---

### Post by xturmn8r on 2007-12-04
I had a similar problem.. I installed vista, so it overwrote the MBR, so I popped in the alternate install CD, and told it to reinstall grub on hd0, it did so, but GRUB didn't find vista. How do I get grub to find the windows install?

---

### Post by xturmn8r on 2007-12-06
nevermind, I found the pertinent info on the /boot/grub/menu.lst. 

it turned out like this:

title		Windows Vista
root		(hd0,1)
makeactive
chainloader	+1

because windows was on the second partition. hope this can end up helping someone!

---

