---
title: "Ugh some stuff that won't work after I restarted..."
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by hilariousness16 on 2007-12-24
I want to get more desktop windows, but it won't let me.

Yes, I did right-click on the desktop window and I did click "Preferences" and selected 4 Columns, but it only shows 2.

My other problem is that my CompizConfig Settings Manager won't load up...

---

### Post by Sef on 2007-12-24
1) Are your columns marked as 1 and your your row is marked as 4?

2) What is your graphics card and system specs?

---

### Post by hilariousness16 on 2007-12-24
Every thing worked before, until I restarted my Laptop -.-

    *  AMD Turion-64 ML-32 (1.8GHz/512KB L2 Cache)
    * 512MB 333MHz DDR SDRAM (1x512MB 200-pin SODIMM)
    * 100GB 4200RPM HD
    * 17-inch Ultra Brightview WXGA+ screen
    * 128MB ATI RADEON XPRESS 200M w/Hypermemory
    * DVD+/-RW/R & CW-RW Combo w/Double Layer Support
    * Windows XP Home
    * Broadcom 802.11b/g WLAN

I got 4 columns, and 1 row.

---

### Post by hilariousness16 on 2007-12-24
and also the "close, maxizie, and minizize" buttons are gone too 

wtf

---

### Post by Afkpuz on 2007-12-24
Hmm.  Well, I know that if you install the compiz settings manager, you must use it to change the number of desktops you have.  Right clicking on the bottom right workspace switcher won't do it.  As for the compiz settings manager not working, can you tell me more? 

1.)  How did you install? via synaptic?
2.) How have you been trying to launch it? (command line?  Alt-f2? Graphical?)
3.) Have you installed you graphics card driver from the restricted driver manager?
4.) Do you have an ATI graphics card?


EDIT:

Try this in the command line

compiz --replace

Does this bring back your close, minimize, and maximize buttons?

---

### Post by hilariousness16 on 2007-12-24
> 

1.)  How did you install? via synaptic?
2.) How have you been trying to launch it? (command line?  Alt-f2? Graphical?)
3.) Have you installed you graphics card driver from the restricted driver manager?
4.) Do you have an ATI graphics card?



 
1) I installed XGL by the Terminal ( Pretty sure lol)[QUOTE=Afkpuz;4010298]Hmm.  Well, I know that if you install the compiz settings manager, you must use it to change the number of desktops you have.  Right clicking on the bottom right workspace switcher won't do it.  As for the compiz settings manager not working, can you tell me more?

2) I usally right click on the screen and press "Change Desktop Backgrounds" then I go to "Visual Effects"

3)Yes

4) ATI Radeon XPRESS 200m (sucks)

So how do I get more work spaces?:confused:

---

### Post by hilariousness16 on 2007-12-24
I reinstalled Ubuntu like 6 times, omg i hate these errors...-.-

---

### Post by dondad on 2007-12-24
> **hilariousness16 said:**
> and also the "close, maxizie, and minizize" buttons are gone too 

wtf


For the button missing problem, try opening a terminal and typing:
```

metacity --replace

```
and see if the buttons return. 

That will return window management to the default metacity.


If that works, then try compiz --replace as noted above.

---

