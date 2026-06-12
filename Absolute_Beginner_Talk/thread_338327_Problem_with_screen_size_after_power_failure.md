---
title: "Problem with screen size after power failure"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by RickHart on 2007-01-14
After any disruption in power the computer re-starts, but everything on the screen is twice the normal size.  It is more than just the font.  What normally is a full screen, I now see 1/2 or less on the screen.  How do I get it back to the original installation size?  I have to reinstall Ubuntu to get it back to normal.
Thanks

---

### Post by riven0 on 2007-01-14
Does doing a xserver reconfiguration help at all? And how about the adjustment buttons on your monitor? That doesn't do anything?

---

### Post by RickHart on 2007-01-14
I am very new at this and don't know what an "xserver reconfiguration" is or how to do it.  Could you explain?  The monitor buttons don't help the problem.
Thanks

---

### Post by riven0 on 2007-01-14
A reconfiguration can be done in the terminal with:

> sudo dpkg-reconfigure xserver-xorg

To get to the terminal, hit CTRL + ALT + F1 and log in.

After reconfiguring, type **startx** and if it still gives you the same problem, try rebooting the comp.

---

### Post by RickHart on 2007-01-14
Thanks, with the weather they say is coming I am sure I will get another power loss and now I have a solution.

---

