---
title: "How to keep monitors alive?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by ADT on 2007-07-25
I've had two monitors die on me in the last 3 months.

The first one went because I had the refresh rate too high I'd say.
It was a 15 inch CRT monitor. About 8 years old.

The next monitor was a 17 inch CRT and I used more conservative settings at a resolution of 1024x768 and Color Depth 16.
It was about 3 years old.

/etc/X11/xorg.conf
```
#Used for Tatung 17 Inch 
        #HorizSync     28-78
        #VertRefresh   50-75
```

I was wondering how would I make my next monitor live longer?

Change the wall socket I use? 
Change the power cable I use?
Don't / Do use an extension lead?
Don't / Do use a surge protection thing?
Turn off monitor and unplug it rather than leave a screen saver on?
Don't use monitor for more than two hours?
Install some sort of software?
Does software or operating systems have any effect on a monitor. ie. xorg settings? That can destroy it?

Forgive my ignorance. :)

---

### Post by tcpip4lyfe on 2007-07-25
Only thing I can think of if get the exact specs as it relates to Hsync and Vsync for your monitor.  Other then that maybe try some of the things your listed.  A strange problem indeed.

---

### Post by dreadlord_chris on 2007-07-25
Your entire system - computer, monitor, & any externally powered peripherals should **always** be plugged into a surge protector - never directly into a wall socket.

---

### Post by Shazaam on 2007-07-25
> **dreadlord_chris said:**
> Your entire system - computer, monitor, & any externally powered peripherals should **always** be plugged into a surge protector - never directly into a wall socket.

Agreed. Preferably one that does line conditioning. You also might look into a polarity(correct wiring) checker ( cheap at hardware stores, plugs right into the receptacle) for the outlets. Improperly wired houses have killed a few electronic components for me:(

---

### Post by ADT on 2007-07-25
Thank you all for the advice. I will check out about a surge protector with line conditioning and a polarity checker.

---

