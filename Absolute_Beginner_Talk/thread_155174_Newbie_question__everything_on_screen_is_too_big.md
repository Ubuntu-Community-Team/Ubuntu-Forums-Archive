---
title: "Newbie question:  everything on screen is too big"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by DanielJapan55 on 2006-04-04
Super newbie here,

Sometimes (about 80% of the time) when I start ubuntu everything is too large: Icons, text, everything.  So I am now scrolling right and left just to read my mail.  I have only had ubuntu for about three weeks, the first week everything was normal size.  What gives? How do I resize everthing back to normal smaller size?

---

### Post by angkor on 2006-04-04
What options do you have in System -> Preference -> Screen Resolution?

Maybe changing the setting in there helps.

---

### Post by WakkiTabakki on 2006-04-04
(dang angkor, you beat me to it with about a second :P)

I'm just guessing here, but check your screen resolution. 
Look in System menu, under Preferences and 'Screen Resolution'. Choose the appropriate value, depending on what computer/screen you've got (1024x768 is sort-of standard for a 15" , 1280x1024 would be standard for a 17-19" screen. If you got a widescreen laptop, it could be 1440x900, or well, anyones guess...)


Another trick (2:nd choice) would be to reduce the font DPI, check under
System -> Preferences -> Fonts 
Then click 'Details' and reduce Resolution. This'll make all text smaller (I like having it around 80 on my 19" TFT).


Now I'm thinking (you say 80% of the time...). Could you have managed to activate the Assistive Tech support, e.g the magnifier... Again, check under System->Preferences (that's generally the place to go :) ) and choose Assistive Technology support, and deactivate it if its on.

Hope it helps
/N

---

### Post by DanielJapan55 on 2006-04-04
I got 640x480.  No other option.  Is there something I need to change in the bios?  I have a 17" desktop.  Weird becuase the screen was fine up until a week ago...

---

### Post by angkor on 2006-04-04
[QUOTE=WakkiTabakki](dang angkor, you beat me to it with about a second :P)
[/QUOTE]

:-D  Well your reply was a bit lenghtier.

Well, it's definately a problem with your resolution. 640x480 is too low especially since you say it used to be normal. Do you remember when it changed? Did you change something in the configuration.

If you're up to it you could read / try this: 

[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

and see if you can change the resolution.

---

### Post by DanielJapan55 on 2006-04-04
and Assistive Tech support was not activated.  Good thought though as I had been opening everything under "system" when I first installed ubuntu trying to learn where everything is.

---

### Post by DanielJapan55 on 2006-04-04
don't know when it changed.  And when it changed it ws a gradual change, sometimes normal sometimes large size.  Now it's doing it everytime.  Wonder if there is a problem with my video card...

---

### Post by angkor on 2006-04-04
[QUOTE=DanielJapan55]sometimes normal sometimes large size.  Now it's doing it everytime. [/QUOTE]

That's very strange. Try the link from my previous post to see if you can fix it. Rember to back up the /etc/X11/xorg.conf file so when you mess up you can always restore your old config.

---

### Post by DanielJapan55 on 2006-04-04
Uh...can you explain what you mean by backing up  using /etc/X11/xorg.conf.  What do I have to do?  I basically have never used the command lines.  My total computer knowledge consists of surfing the net.  Talk to me like a total beginner please.

---

### Post by WakkiTabakki on 2006-04-05
The file 
```
/etc/X11/xorg.conf
```
contains the information needed for Linux/Ubuntu to set up the user interface, like mouse, keyboard, screen etc...
If you've borked something in this file it's likely that your graphic UI won't start (i.e you'll be happily greeted with a horrendous error message when you boot). So make a copy of the current file which you can revert to if something goes haywire:
```
cp /etc/X11/xorg.conf ~/xorg.conf_Backup
```

Then it time to hack the xorg-file!
```
sudo gedit /etc/X11/xorg.conf
```

You should be able to read what to do under the link angkor posted. Or post the sections 'Device', 'Screen' and 'Monitor' here, together with what graphics card you've got and we'll try to figure out whats wrong...

EDIT: Oh yeah, are you on Gnome or KDE?

Cheers
/N

---

