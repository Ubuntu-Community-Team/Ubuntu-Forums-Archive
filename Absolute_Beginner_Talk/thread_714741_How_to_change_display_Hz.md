---
title: "How to change display Hz ?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by -random on 2008-03-04
When i go to:
System > Administration > Screens and Graphics > Model

I can't find the driver for my BenQ FP92e, but i've read on the forums that the driver doesn't actually matter...

My monitor is made to display 60/70/75 Hz, but it's displaying 72Hz at the moment! This gives me a 'nonpreset mode' error a lot, which is rather irritating :P

How do i change my display output frequency?:confused:

:guitar::guitar::guitar:

---

### Post by CaptainCabinet on 2008-03-04
The way I do it is go to System > Preferences > Screen resolution. 
Your System menu sounds different from mine though so it might not be in the right place.

---

### Post by paul.matthijsse on 2008-03-04
Hello, have you activated the limited supported drivers? It's under System - Admin. That might help.

---

### Post by -random on 2008-03-04
limited drivers are enabled.

The 1280x1024 lcd panel only gives me the following resolutions:

57 61 70 71. Which is nice, but i need a 75Hz option because:

When i launch a wine app the output is 72Hz. (Is this 72hz output a wine problem?)

Somehow it's running at 60Hz at the moment :-k Which is cool for ubuntu and normal apps etc..

I've tried the normal monitor (not lcd) which gives me the 75Hz option, but the display is all hazy at the logon screen and it auto-adjust at each boot and also i don't think your'e supposed to use this option on a lcd screen.

Maybe there's a file like xorg.conf or something where i can edit my Hz? (or even the wine output Hz? )

---

### Post by mozetti on 2008-03-04
Yes, you can edit the xorg.conf file. Or, I recommend opening a terminal and running:```
sudo dpkg-reconfigure xserver-xorg
```
Choose the Advanced set up option and at some point it will ask you for the hsync and vsync ranges. These should be found in the monitor's manual or on the product's website.

---

### Post by -random on 2008-03-05
Close! but no cigar..

My screen is running at 76Hz instead of 75Hz.... but it doesn't give me a 'nonpreset mode' when i turn it off and on.

Thankx for the help so far!

How bad is 'nonpreset mode' for you lcd?

o ye, the modes for Hz i can select now from sys > admin > screens&graphics are now 50,55,56 and 57Hz

---

