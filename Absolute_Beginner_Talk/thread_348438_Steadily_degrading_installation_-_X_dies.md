---
title: "Steadily degrading installation - X dies"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by jim h on 2007-01-28
I guess one other person had problems with ubuntu and found his flakey memory.  I think this is different.  My installation has been steadily deteriorating for a week, to the point where I now have to enter recovery mode, startx as root, bring up a terminal to su to my account, and run everything from there.
  When I try a normal login it gets most of the way through building the desktop and then X dies.
  At first, every other time.  Then 2 out of 3.  Now every time.  Not always at the same point, though.  Sometimes it restarts spontaneously.  Sometimes I can Ctrl Alt Backspace or Del.  Mostly not.
  Once I noticed the CPU was at 100% and this was something called xflock (I think).  I killed it and was fine.  Why was a screensaver running at login?
  When I did get it working it would (while my back was turned) go screen black and sometimes a keypress would bring it back and sometimes not.  Then it's push reset.
  I have seen that X (or someone) knows how to turn my monitor on and off, but this never happens when I would expect it, and the screensaver and power management offered nothing but "do nothing" or "hibernate".  I stayed with do nothing, but I am not sure that worked.  I hibernated once,  that's roughly when the trouble started.
  Why does everything seem to be fine when I get here as root?
  Shall I reload it yet again, or does someone have any suggestions?
  PS, I used this exact hardware and Bios except for the HD for a couple of years with RH7, so I think that should be okay.
  TIA, any suggestions greatly appreciated.

---

### Post by maino on 2007-01-28
I would suspect the hardware in your case.

I had the same kind of problem once; a steadily deteriorating OS (not ubuntu at that time), failing at random times.  I understand.  It is irritating.
Eventually found that the capacitors on the mother board had blown up.

Check the HD first, (fsck or something?), and you might want to take a look at your mother board, too.

---

### Post by jim h on 2007-01-29
Whoa.  Impressive.  The capacitors?  That's down to the nitty!!!
   I will check it out - it sounds right
  Thanks.

---

