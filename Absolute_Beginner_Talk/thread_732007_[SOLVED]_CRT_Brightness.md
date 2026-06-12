---
title: "[SOLVED] CRT Brightness?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by joshdudeha on 2008-03-22
Um, I know having a CRT is bad - but I have no money to get an LCD at themoment, and they are like a few hundred quid atm.

so im stuck with this atm.
I want to know if there's anyway to make my screen brighter? Using some app or something because the brightness dials actually on the monitor are max. but its dark as anything.

Can someone **please** help?

---

### Post by Sam Lars on 2008-03-22
Have you checked all of the settings on the monitor?  One of my CRTs has a "video level" setting, and it affects the brightness... also, is the contrast setting causing it?
What kind of video card do you have?

---

### Post by herbster on 2008-03-22
Yeah if you've got an Nvidia card you should be able to use nvidia-settings and adjust the brightness from there.

---

### Post by joshdudeha on 2008-03-23
I just have an on-board intel 64MB card =/
And there isn't any brightness or contrast setting on my desktop?
any more ideas?
Thanks anyway

---

### Post by Sam Lars on 2008-03-23
I didn't mean on the desktop, I meant on the monitor.

---

### Post by joshdudeha on 2008-03-23
Oh, there are controls on the monitor, but they are all as high as the y will go, I've tried all sorts physically =/

---

### Post by joshdudeha on 2008-03-28
Can anyone help?
It's so dark.

---

### Post by joshdudeha on 2008-03-28
YESS!!
Found out how to do it.

In the terminal type: xgamma -gammer x.x
where x.x is the number of gamma.
Mine is 1.5 now, looks great again.

Might build a graphical tool so that less aware users can brighten their screens without using the cli, or knowing the commands.

---

