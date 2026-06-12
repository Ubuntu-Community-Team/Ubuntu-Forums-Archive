---
title: "Reinstalling OSX..."
date: 2006-09-08
forum: Apple PPC Users
---

### Post by joyflop on 2006-09-08
Hi!

After spending a few happy months with Ubuntu on my pc, today I decided to install it on my iBook G4 (ppc). I thought it would be just as easy, but it hasn't been & I'm just not as pleased with the results as I have been with my pc tower.

Long story short, I have decided to reinstall OSX, but I can't get it to boot from the OSX install disk (neither 'c' or 'option' keys are loading the disk). If this matters, when I installed Ubuntu, I erased the HD. I've searched the forums but I haven't found anything applicable yet.

Does anyone have any advice/tricks/pointers for reinstallation? I'm still quite new to things like terminal and the like, so simple language is best :)

Thank you!

---

### Post by kyteflyer on 2006-09-08
OUCH!  I'll be watching this thread closely as I have also installed to an iBook G4.  It never occurred to me that reinstalling OSX would be a problem.

Re using Ubuntu... I think if ever I would have PC hardware again, I won't hesitate to use it on that, but it hasn't got the same pizazz for me on the iBook.  Mind you, its working very well except for wireless networking and sleep mode, which I have not dared try.

Reinstalling OSX was on my list of to-dos for today though... so I hope someone has a solution (or perhaps I might find one, myself.  I'll let you know)

---

### Post by paradox963 on 2006-09-08
There are 2 things I could suggest the first would be to reset the pram if you have not yet done so restart and hold appple+option+p+r till the unit chimes 3 times. Then try booting off the CD if that does not work and if you have another Mac you could boot your ibook into target disk mode and then use the other machine to reinstall. Best of luck

---

### Post by kyteflyer on 2006-09-09
Paradox is right about using a PRAM reset to get things happening.

Timing is everything, though.  I have done it successfully today and even as we speak, OSX is downloading its updates.

1. Tell ubuntu to restart.  As it starts shutting down be ready to hold down Apple - Option - P - R BEFORE you hear the first chime.  If you hear it, its already too late and you need to start again.

2. As Paradox says, you need to let it chime.. not 3, but FOUR times.

3. After the last chime and before it starts rebooting, let go the four keys you have been holding down, and switch to hold down your "c" key until you see the Apple symbol on screen.  Installer will now load.

4. From within the installer, call up disk utility and delete the partitions created by Ubuntu, reformat as Mac extended journaled.  Quit out of disk utility.  You might need to restart again, I did not.

5.  The install should proceed fairly painlessly (if slowly, Installer needs to check disk integrity) from there on.

Good Luck!

---

### Post by joyflop on 2006-09-09
I'm happy to say that zapping the pram seems to have done it. I'm reinstalling Tiger now. 

I think I will be sticking to pc + ubuntu, ppc doesn't seem to work as well with ubuntu yet. It was a learning experience though :D

Thanks again, kyteflyer and paradox963!

---

