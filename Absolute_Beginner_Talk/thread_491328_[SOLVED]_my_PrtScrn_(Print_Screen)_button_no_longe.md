---
title: "[SOLVED] my PrtScrn (Print Screen) button no longer works"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-07-03
Hello,
My Print Screen button on my keyboard used to work. But now, it's not working anymore. How can I fix this problem? Thanks.

---

### Post by starcraft.man on 2007-07-03
> **hanzj said:**
> Hello,
My Print Screen button on my keyboard used to work. But now, it's not working anymore. How can I fix this problem? Thanks.

If it ceased working now, I can only assume its a key jam/dirt (unless you did something software wise to remove the function). Pop off the cover of the key and check that its ok underneath.

---

### Post by hanzj on 2007-07-03
Is there a less-intrusive way to check?

---

### Post by starcraft.man on 2007-07-03
> **hanzj said:**
> Is there a less-intrusive way to check?

Do you have x ray vision? Otherwise, no. I've never heard of anyone turning off their print screen key's function by accident or intentionally via software so my first reaction is to assume hardware failure.

Just take a lil knife and slip it down the side then pop it out, almost all keyboards I know have removable keys for cleaning and such.

If you have a dual boot I suppose you could boot into Windows and see if it works there. It's not too scary popping keys off though :).

---

### Post by hanzj on 2007-07-03
If I have to do that, I will. But perhaps, I can try mapping a program to open with that key. And then seeing if pressing that key works.

Or, I could check whether print screen (the program, not the key) works some other way.

---

### Post by hanzj on 2007-07-03
Or perhaps I could remove the screws from the back, no?

---

### Post by starcraft.man on 2007-07-03
Do you have an irrational fear of popping keyboards keys poking out your eye or something? Is this keyboard lined with gold or something else precious? Seriously, the keys are made to go in and out in most models. I have a friend I know who pops each and every key out yearly and cleans it all. One key won't kill ya :p

Oh and the screen shot program it relies on I believe is the same one as default in GNOME. Applications > Accessories > Take Screenshot. I assume that works properly.

---

### Post by hanzj on 2007-07-04
Yes, Applications > Accessories > Take Screenshot works properly.

---

### Post by hanzj on 2007-07-04
Ok. I popped it off, and I don't see any dirt. It looks clean.

I ran "xev" program in CLI/terminal. When I pressed the PrintScreen Button, xev was able to "hear" it. So we can conclude that the hardware is fine. The problem lies with my ubuntu.


SOLVED: 
Solution at [http://ubuntuforums.org/showthread.php?t=492458](http://ubuntuforums.org/showthread.php?t=492458). (Quick answer: Keyboard Shortcuts)

---

