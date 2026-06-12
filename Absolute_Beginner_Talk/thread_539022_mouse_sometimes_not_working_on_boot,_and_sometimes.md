---
title: "mouse sometimes not working on boot, and sometimes stops working randomly."
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by graigsmith on 2007-08-30
so. sometimes i will boot my computer up, and get to the login screen and realise, hmm. the mouse isn't working.  so then i reboot it and then it works

and sometimes when i launch wow, thru wine, the mouse suddenly stops working. and then i have to reboot.

it's a weird problem, and i dont know how to start figuring this one out. :confused:

---

### Post by Mark_in_Hollywood on 2007-08-31
I'm having the same or very similar problem. Sometimes, the mouse vanishes off the screen and won't come back for several seconds. Sometimes the KB and mouse lock up and the system must be warm booted. I'm only adding this post/thread so that I can find it later on.

Out of curiosity have you ever flashed your BIOS?

---

### Post by graigsmith on 2007-09-02
AHHHHHHHHHHHHHh it did it AGAIN!!!!!  wtf.   does anyone have any idea why this is happening?

---

### Post by graigsmith on 2007-09-02
if i hit ctrl alt backspace to restart x, it wont start because it cant find the mouse. yet i can see the mouse in /dev/input  and i can also use sudo cat mouse  and move the mouse around and see it picking up stuff.  

anyone have any ideas?

---

### Post by dpar on 2007-09-02
My mouse will not work if I reboot from windows into Ubuntu. I have to actually shut the computer off in windows, then boot to ubuntu. This doesn't happen when rebooting from any other OS's (Linux), just Windows.
I think sometimes windows doesn't release the hardware properly.
This may not pertain to you though.

---

### Post by graigsmith on 2007-09-03
no, i'm only using linux.   i wonder if it has anything to do with my motherboard.

---

### Post by graigsmith on 2007-09-06
ok. it did it again!!! wtf?  right when i open wow via wine. the mouse just stops working. my wacom tablet still works.  but dangit. is there anyone who knows how to troubleshoot something like this? when it happens a ctrl-alt-backspace wont go because it actually cant find the mouse anymore until i reboot. what's going on here?  and the light on the mouse is still on.

---

### Post by Kralnor on 2007-09-08
I have a similar problem. The cursor keeps getting displayed but the mouse simply doesn't work at all.

This both happens at boot and at other times when the computer has been inactive for a while.

I have a suspicion that it might be the mouse itself that has some sort of hardware failure (it's really old, nearly eight years) because I don't recall having the problem with previous mice used on the very same setup.

Oh and re-plugging the mouse into an USB slot always makes it active again.

---

### Post by graigsmith on 2007-09-09
hmm occasionally mine doesn't work on boot either.

replugging doesn't work.

i have plugged the mouse into a different socket. and im hoping that fixes it.  if that's the case mabey my motherboard is going bad.

---

### Post by Kralnor on 2007-09-09
I have come to the conclusion that the mouse itself is defective somehow. Several other mice have been tested on the same box and none of them have had the same issue.

It was really old anyway ;)

---

### Post by graigsmith on 2007-09-10
hmm. plugging the mouse into a different socket doesn't help.  mabey my mouse is defective also. 

but dangit. it just cant be, because it always happens when i start wow via wine.  so it HAS to be some kind of software issue.

---

### Post by toasterofirony on 2007-09-10
Borrow a friend's mouse and try that, just to be sure :)

---

### Post by graigsmith on 2007-09-10
hmhm. i think i might have fixed it. i think it had something to do with they way i had my xorg set up.  instead of using the mice device, i was using the mouse1 device. you were supposed to do this for the wacom tablet driver, but it seems like when i do this the tablet works great. so gonna try this for a while and see how well my mouse works.

---

### Post by eagletip on 2007-09-10
Hellllooooo there.....

I have an old pentium. Tried to install feisty onto it and the same problem arises. Boots up ok, and installation can be done to a certain point with the key board, ( as I do not know all the short cuts) but the cursor is displayed and mouse will not move. I have bought a brand new mouse and works fine on my other computer but refuses to work on the pentium one. The mouse is good. So therefor I cannot complete the install.
So any ideas on that?????

Please don't be shy, any help is appreciated lol

---

### Post by graigsmith on 2007-09-10
eagletrip, try the alternate install CD.  odd's are on an old pentium im suprised that it even booted on it.  the live cd loads everything into ram. and im betting it doesn't have enuf ram.  

the alternate install is all text mode. but it shouldnt have any problems installing.

---

### Post by eagletip on 2007-09-11
hey graig
thanks for the up. Ill def try it. Ill post again with results as soon as I can process.

---

### Post by eagletip on 2007-09-12
OK so here goes.
I did as suggested, It did install quite easily however the system will not let me use my mouse:( 
Wich I knew all the short cut keys so I could possibly diagnose the prob.
Any more ideas out there?????

---

### Post by graigsmith on 2007-09-19
problem solved, turned out my motherboard went bad, and later on my hard drive refused to boot, and that drive wasn't bad.   i think the ide part of my motherboard went bad, and somehow that interfered with the mouse.

---

