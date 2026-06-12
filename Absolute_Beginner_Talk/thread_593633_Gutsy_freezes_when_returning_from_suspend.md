---
title: "Gutsy freezes when returning from suspend"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by baba_oreilly on 2007-10-27
I just installed Gutsy on my laptop (dell inspiron 630m). I was hoping this issue would be fixed by the new release (it used to happen in feisty too) but since it hasnt, I'm farming it out to the forum. Basically, I close the laptop lid to suspend, and sometimes (I cant tell any consistent pattern of when this happens) when i open the lid to wake it back up, the keyboard and mouse are frozen. It asks me to reenter my password as usual and the cursor is flashing, so I dont think the computer is actually locked, it just seems that it forgot that the keyboard and mouse exist and I have to do a hard reboot. Any ideas?

---

### Post by Pumalite on 2007-10-27
Whats the size of your /swap compared to your RAM_

---

### Post by baba_oreilly on 2007-10-27
swap is 1GB, RAM is 512mb

---

### Post by khurrum1990 on 2007-10-27
does this consistently happen and which vga card r u using?

---

### Post by baba_oreilly on 2007-10-27
Its not consistent... maybe once or twice in every ten times. And I cant figure out if theres anything consistent thats triggering it. I *think*  every time its happened, I suspended while firefox was open, but then again, firefox is probably open about 90% of the time im using the computer and I've definitly successfully unsuspended numerous times when firefox was open. 

My laptop doesnt have a video card - just integrated intel graphics. 915G i believe.

---

### Post by baba_oreilly on 2007-10-29
Bump... Anyone have any ideas?

---

### Post by Ruby.Tuesday on 2007-11-05
Same thing is happening to me.  I have a Toshiba Tecra A2 laptop with an Intel 855 type video card and 2GB memory and a further 1GB of swap.  

The laptop was originally installed with Feisty which worked flawlessly.  After upgrade to Gutsy, I started to have occasional problems with the system going into suspend mode and not coming out afterward.  This doesn't happen every time but seems to be related to being suspended for an extended period of time (> 1hour).

Any thought or suggestions would be appreciated.

---

### Post by Pumalite on 2007-11-05
In laptop, for hibernation: /swap has to be equal to RAM

---

