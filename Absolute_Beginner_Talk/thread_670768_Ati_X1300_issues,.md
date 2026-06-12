---
title: "Ati X1300 issues,"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Charred one on 2008-01-17
Hi, I am fairly new to using Linux. Therefore don't really know what I am doing very well.

 I have an Ati Radeon X1300 video card, and have been having some trouble with it. I  supposedly have it installed correctly, and even have Compiz Fusion working with full desktop effects. However the moment I try to play any game (Xmoto for example) the screen goes black, and I have no idea how to stop the program without forcing my computer to restart. Furthermore sometimes I get weird little horizontal lines on my desktop on the bottom right corner, most times it seems to be after I have been using Firefox. So I was hoping someone out there might know what the problem is;  or even just how to force the program to stop (like with windows using Ctrl+Alt+Del)

Thank you for your time.

---

### Post by rufius on 2008-01-17
Its recommended that you don't try to play any graphically intense games while Compiz Fusion is running. A lot of times it can cause conflicts so you'll want to disable those before you start your game.

Try that out and see if it improves anything.

Hope that helps :)

---

### Post by peitschie on 2008-01-17
Definitely disable compiz.  Which games are you running?  Are they wine (Windows) games?

To kill the game, sometimes you can do CTRL+ALT+BACKSPACE.  This will kill the X session and log you out, but may start it.

The other thing you can do to "safely" reboot the computer if CTRL+ALT+BACKSPACE doesnt work is to hold CTRL+ALT+Print Screen(SysRq on some keyboardS), and type in the following one letter at a time: R E I S U B  (pause about 5s between each key press).  This will shut linux down safely and reboot it :)

---

### Post by Charred one on 2008-01-18
Hey thanks for the advise, I did not know that Compiz should be disabled to play games. Sadly it did not fix the problem, but it certainly might have narrowed things down a bit.

---

### Post by Charred one on 2008-01-18
Ctrl+Alt+Backspace worked perfectly, thank you. I have not had time to learn as much as I would like, and think that perhaps it is time I started.

---

### Post by peitschie on 2008-01-18
The ATi drivers have always been a little shifty under linux...  I wouldn't be surprised if it is just a problem with that.  Are you trying to run games built for linux or games built for Windows (via wine)?

---

