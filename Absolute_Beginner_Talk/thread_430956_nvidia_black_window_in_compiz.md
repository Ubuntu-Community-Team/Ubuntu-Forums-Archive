---
title: "nvidia black window in compiz"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by mlhudson on 2007-05-02
is there anything to be done if my windows freak out and i get lots of black windows & menus while compiz/gldesktop is running?

i used info from this forum to get the thing working _with the top bar_ and _with a usable terminal_. great stuff! 

yet, now i get frequent, and intermittant black windows. the posts i've read attribute this to the nvidia drivers. many folks give tips for a fix while using beryl, but i'm using the standard feisty compiz & the gl desktop preference gui.

my system is a toshiba satellite laptop, nvidia geforcefx 5200 32MB (please don't laugh out loud, the laptop was free from a friend).

---

### Post by orb9220 on 2007-05-02
The Black window is also associated with running out of video ram. Mx fx5200 with 128mb runs great until I have firefox,Nautilus,Transparent Term window,Amarok,etc.. running just fine until I run too many then they start to go black. 

If I want to really get a black window all I have to do after have those apps running is to open Google Earth and then I get black windows because I have just run out of video ram.

If you open and close individual windows and they run fine ever time. And only happens at the 2,3,4th window opening it just means you have run out of video ram.

What did you expect for a 32meg card?

---

### Post by mlhudson on 2007-05-02
thank you for the blunt honesty :) at least i know it's not just a check box i didn't untick.
blessings

---

### Post by RAH66 on 2007-06-26
lol gr8 I have the same problem is there no way that compiz  can use sytem ram when it runs out of video ram coz I have 2 gigs worth and at most 30% of it is used when running a **** load of apps, windows etc. :(

---

### Post by phr0ze on 2007-06-28
I have a friend with a card with 128MB that says he never has this happen. How can this really be related to ram?

---

### Post by testube_babies on 2007-06-28
In Beryl, you can choose the "Force AIGLX" rendering mode to eliminate this problem.

It's been a while since I've used compiz, but check the manpages for compiz and compiz.real to see if it gives you a similar option (something like indirect rendering?).

---

### Post by testube_babies on 2007-06-28
> **phr0ze said:**
> I have a friend with a card with 128MB that says he never has this happen. How can this really be related to ram?

It really IS related to ram, but it's a bug in the nVidia drivers, so it only affects nVidia systems.  The problem has been reported to be fixed in the next (currently unreleased) 100-series driver.

---

### Post by RAH66 on 2007-06-29
LOL well I needed an excuse to get the latest of the 8800 series hmmmmmhmmmm!!! :D

---

