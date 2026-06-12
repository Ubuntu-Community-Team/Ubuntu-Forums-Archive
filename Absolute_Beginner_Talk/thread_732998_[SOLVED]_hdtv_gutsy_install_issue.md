---
title: "[SOLVED] hdtv gutsy install issue"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by prophetk on 2008-03-23
ok so from what i have been able to find in the forums, i can't quite get an answer...

i am attempting to install gutsy on a pc that is currently using my hdtv as a monitor (it is a viewsonic screen, and windows xp ran completely fine on it, no issues).  but when i boot from the live disk, i see half a screen, and not the half that i can work with.  i already attempted to change the resolution, but that did not help.  any ideas?

---

### Post by gobbles414 on 2008-03-23
> **prophetk said:**
> ok so from what i have been able to find in the forums, i can't quite get an answer...

i am attempting to install gutsy on a pc that is currently using my hdtv as a monitor (it is a viewsonic screen, and windows xp ran completely fine on it, no issues).  but when i boot from the live disk, i see half a screen, and not the half that i can work with.  i already attempted to change the resolution, but that did not help.  any ideas?

Is you're HDTV a 720p, 1080i, or 1080p? Also, please post some details about your PC's graphics hardware and which version of Ubuntu you're trying to install. If you can get to the command line, try going *sudo dpkg-reconfigure xserver-xorg*. Another option is to try the installation with an *Alternate CD*. There's a checkbox on the Ubuntu downloads page that will switch your download from a LiveCD to the Alternate. Lastly, you may wish to try installing Ubuntu 8.04 beta.

---

### Post by prophetk on 2008-03-23
i can't get far enough in to get into the terminal.

i have a dell dimension 3000 with an intel celeron 2.4GHz processor, 254mb ram and an 80gb hard drive. 

it is a 1080i ViewSonic N2635w hdtv.  I am currently using the vga input to have it attached to the computer.  

and i was attempting to install 7.10 (gutsy)

---

### Post by prophetk on 2008-03-23
ok for some reason or another, my tv was resetting the horizontal positioning to 0 so it shoved the screen all the way to the left.  for whatever reason, this was not the first thing that came to mind.. but this is why i'm in the beginner thread :D  

so for anyone who might have been having the same problem, all i did was adjust the horizontal positioning until the screen came back to the right place.  i am still not sure why it did this with the install cd, but either way, i just didn't think of the simplest answer to fix it :D

:KS

---

### Post by gobbles414 on 2008-03-23
> **prophetk said:**
> i can't get far enough in to get into the terminal.

i have a dell dimension 3000 with an intel celeron 2.4GHz processor, 254mb ram and an 80gb hard drive. 

it is a 1080i ViewSonic N2635w hdtv.  I am currently using the vga input to have it attached to the computer.  

and i was attempting to install 7.10 (gutsy)

Your PC is on the boundary between using the LiveCD and Alternate CD for installation of Ubuntu 7.10. Click [here]("https://help.ubuntu.com/community/Installation/SystemRequirements/GutsyGibbon") for more info. Also, your computer is using *Intel Extreme Graphics 2* integrated graphics. To be honest, I'm surprised that your HDTV worked well in Windows XP with your integrated graphics. But if it worked in XP, it can probably be made to work well in Ubuntu too. Please try installing with the Alternate CD and then report your progress.

EDIT: I see that you've solved your problem! If you encounter any more graphics-related difficulties in the near future, post them in this thread.

---

