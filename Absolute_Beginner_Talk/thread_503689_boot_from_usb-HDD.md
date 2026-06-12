---
title: "boot from usb-HDD"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by veebee on 2007-07-18
kubuntu from usb-HDD
I run kubuntu 7.04 64bit on 3 desktop machines, but I have tried to install on a usb HDD to use my partners XP machine at night to crunch seti.

It has seemingly installed OK, but when I try to boot, it gets 3/4 way through "normal" boot and then goes to text screen.

Runs some sort of file system check, with avahi daemon "failing" but continues.
Then, 2 lines later it hangs at "starting cupsd".

keyboard is active but the boot process goes no further.

If I boot in recovery mode, it goes right through to a command prompt, and when I type"reboot", it goes through the same thing as above.

I do not wanto print, so is there some way I can get rid of/ bypass cups ?

---

### Post by Keen101 on 2007-07-19
sudo apt remove cups might work.  or is it sudo apt remove cups*? or is sudo apt remove *cups?


I think it is the second one. (the star is so apt removes everything with "cups" in the name) or it might be sudo apt remove *cups*. 


not an expert, so I hope someone else replies.


hope it helps anyway. :)
-keen101

---

### Post by Keen101 on 2007-07-23
I am planning to do what you are doing. Install Ubuntu to an external Hard Drive, so it can be portable. But, for me I will wait for gutsy, because I have heard it will have better plug and play and hot swapping support.



-keen101

---

