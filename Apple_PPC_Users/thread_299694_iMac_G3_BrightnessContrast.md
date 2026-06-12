---
title: "iMac G3 Brightness/Contrast"
date: 2006-11-14
forum: Apple PPC Users
---

### Post by Osiris23343 on 2006-11-14
As far as i can tell there is no way to adjust the brightness/contrast through Dapper Ubuntu.  A through Google search on the issue tells me to reinstall OS9 and change it there, but as this is a hand me down computer i don't have the original cds.  Are there any solutions to this problem?

The Computer is a slot loading iMac g3, with 256mb of ram.

---

### Post by Osiris23343 on 2006-11-15
*bump*
Anyone?

---

### Post by DirtDawg on 2006-11-15
You should be able to adjust the brightness and contrast through a GUI. I'm not in front of my Linux box right now, but it has Xubuntu(which I recommend for g3) on it and I believe those adjustments are under Applications>Settings>Display or something similar. 

If you're asking about a way to adjust brightness/contrast using the hardware built on the actual imac, then you may be out of luck. I don't remember ever seeing those knobs on mine.

---

### Post by Osiris23343 on 2006-11-16
right now it just has Ubuntu, which runs fine on my other g3s.  as far as i can see theres no brightness in Ubuntu, but ill put in xubuntu and see if it changes anything

---

### Post by DirtDawg on 2006-11-16
> **Osiris23343 said:**
> right now it just has Ubuntu, which runs fine on my other g3s.  as far as i can see theres no brightness in Ubuntu, but ill put in xubuntu and see if it changes anything

I recommended Xubuntu only because you will find it runs faster than regular Ubuntu, but it does not have as many features. But Ubuntu should also have a GUI for adjusting screen settings.

Now I am in front of my linux box. The display controls are under Applications>Settings>DisplaySettings on Xubuntu. What appears is a set of 3 sliders labeled 'r' 'g' 'b'. Turning these up adjusts the brightness of the screen. I am almost certain Ubuntu has something similar to what I've described and likely something more advanced. Try looking around a little before you start over.

---

### Post by DirtDawg on 2006-11-16
I just had another thought(more of a 'duh' moment, actually).

You can install Xubuntu without reinstalling the entire system. Open a terminal and enter:
```
 sudo aptitude install xubuntu-desktop
```
Then when you log in, press the "session" button and change it to "XCFE" or "Xubuntu" (I'm not sure what name it uses, but they're the same). If you don't like Xubuntu, you can uninstall it or at least never use it.

Anyway, I'm not sure any of this will address your original problem. I hope you get that figured out. Good luck.

---

### Post by Osiris23343 on 2006-11-16
you are right, xubuntu is faster.  I guess i need contrast.  Thats the problem with these imacs... they try so hard to be simple that they omit the little things like brightness, contrast, and dimension buttons on their monitors.

---

### Post by DirtDawg on 2006-11-16
I found a couple packages you might be interested in.

The first is [xvattr]("http://packages.ubuntu.com/edgy/x11/xvattr"), and is available through Synaptic. It looks like it deals directly with contrast, but it might be a little complex(although I think there's a GUI interface). In addition, it apparently needs to be run every time you boot up. It's easy enough to have things run on boot up, if you need help just ask, but getting the adjustments you want might take some experimentation.

The other is called xgamma, which should also be available through Synaptic. There's a thread about it [here]("http://www.linuxquestions.org/questions/showthread.php?p=2485382"). I'm not certain it will address your contrast problem. It might. 

Once again I'm not in front of my Linux box so I can't fiddle at the moment and I've never used either of these. Nontheless, I hope this helps. 

I totally agree. It's too bad that, for all their slick designs, Apple negleted such an obvious thing like monitor knobs.

---

### Post by Osiris23343 on 2006-11-16
the xvattr doesnt seem to do anything.  The gamma switch does make it brighter and at least make the console readable, so i don't need an external CTR anymore.
Im going to follow a hardware lead with the CRT adjustments. If you dont hear from me its because i electrocuted myself ;)

---

### Post by Osiris23343 on 2006-11-16
I have resolved the problem.
First i had to take off the clear plastic part of my imac, and adjust the CRT screws to sharpen it and change the brightness levels.  The resolution and color were still off, and i used xvattr to correct the color levels.  Now it looks pretty good, not brand new, but definately operational.  Thanks!

---

### Post by DirtDawg on 2006-11-17
> **Osiris23343 said:**
> I have resolved the problem.
First i had to take off the clear plastic part of my imac, and adjust the CRT screws to sharpen it and change the brightness levels.  The resolution and color were still off, and i used xvattr to correct the color levels.  Now it looks pretty good, not brand new, but definately operational.  Thanks!

:KS :KS :KS Wow, great work! Glad I could help. :KS :KS :KS

---

### Post by jasonli on 2007-04-03
Hey guys,

Is there anyway to access the open firmware directly, by pressing Cmd + Opt + O + F when starting the machine, and type something in the command line interface of apple's open firmware there to adjust th brightness/contrast/geometry?

It is too stupid that we have to install the whole os 9 system, only for screen adjustment...

---

### Post by dinkust on 2007-04-05
To adjust the screen brightness on an ibook I hold the Function key and hit F2 or F1.  I hope this helps!

---

### Post by jasonli on 2007-04-06
This won't work for iMac. There is no Fn key, and even in a mac os, the screen settings are done in softwares, not through shortcut keys...

BTW, it seems my ubuntu does not recognize the F11 key, e.g. does not turn to full screen in Firefox by hitting f11.

---

