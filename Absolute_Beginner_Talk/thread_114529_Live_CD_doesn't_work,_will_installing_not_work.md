---
title: "Live CD doesn't work, will installing not work?"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by DayZero on 2006-01-08
Hey there, I just recieved my CDs in the mail and tried the Live CD and it didn't work... does that mean the install won't work either or is the LiveCD limited at all in anyway?

Everything goes fine up until the GUI with the live CD, it goes through all the setup and detecting stuff, and then displays the Ubuntu splash screen, but when it goes to enter the GUI the screen gets all garbled with weird lines/colours etc.

graphics card is an XFX GeForce 6600 256MB AGP
mobo is an nforce2 (ASUS a7n8x deluxe)
processor is amd athlon 2700+

I was using the x86 LiveCd...

Anyways... the question is should I bother installing ubuntu? is it just my particular vidcard (it was sort of cheap... is XFX a bad brand)? is it just the LiveCD? or is there something else I might be doing wrong?

---

### Post by Terry of Astoria on 2006-01-08
I don't know about your particular board and setup. I can tell you that I've seen cases where the live CD acted just like you say, and still the installer worked fine. 
I have an NForce board from MSI and it works well. You appear to have an Nvidia graphics chip. I guess that would work OK too. there are drivers available, as far as I know. You may be able to tweak a few settings and get it to work even if it doesn't at first.

---

### Post by aysiu on 2006-01-08
It's not worth installing if the live CD won't work.
Maybe you can work with the live CD a bit, though.

When it's all garbled, press control-alt-f1 and type ```
sudo dpkg-reconfigure xserver-xorg
``` and follow the prompts. Any difference?

---

### Post by DayZero on 2006-01-08
> sudo dpkg-reconfigure xserver-xorg


okay I tried that, and went through the config... it recognizes that it's nv, which I'm assuming is nvidia, and that it's a geforce 6600GT... when I finish going through all the other stuff it just goes back to the command line. what then?

---

### Post by Terry of Astoria on 2006-01-08
type
startx
at the prompt

---

### Post by aysiu on 2006-01-08
[QUOTE=Terry of Astoria]type
startx
at the prompt[/QUOTE] Before that, try control-alt-f7

---

### Post by DayZero on 2006-01-08
> try control-alt-f7

Ok, goes back to the garbled screen.  Does this mean that ubuntu doesn't support my video card?

> type startx

It says that xserver is already running on display 0 or something like that...

---

