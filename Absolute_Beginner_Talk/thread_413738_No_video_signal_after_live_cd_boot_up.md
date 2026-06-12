---
title: "No video signal after live cd boot up"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by blinkme on 2007-04-19
Hi, I am a long time Windows user finally making the switch to Linux. I downloaded 7.04, burned to cd at 8x, and tried to boot with the livecd. Initially everything works fine, but after the splash progress bar finishes, i see a couple clicks in the top left and then get a "no video signal" notice on my monitor before being treated to a black screen. 

Any ideas of how to fix this problem, I really want to try Ubuntu. Here's my system:

A64 2.6ghz
1gb DDR2 667
80gb SATA drive
X1800 GTO
1440x900 Acer LCD

Thanks for the help

---

### Post by blinkme on 2007-04-19
bump

---

### Post by K.Mandla on 2007-04-19
If you press ALT+F2 (or F3 or F4 or ...), do you get a terminal window? It's possible Ubuntu picked the wrong driver for your card, in which case it's fairly easy to fix.

---

### Post by s9am_me on 2007-04-19
I have the same problem trying to load it on my desktop.  My laptop worked fine so I know its my desktop hardware.  I have the same vid card (ATi x1800xt) and a 19" WLCD (1440x900).  I think Ubuntu doesn't pick the right resolution and refresh rate which results in the monitor not receiving signal.  It picks something that's out of the monitors range.  I haven't not found a fix yet.  I tried getting into a terminal, but the screen is all garbled with pink and green lines across the screen.

---

### Post by cawill on 2007-04-19
Can you get the shell up (alt + ctrl + f1)?

If you can then you should be able to type:
dpkg-reconfigure xserver-xorg
This will allow you to manually select the driver and resolution/ refresh rates.

Hope this helps.

---

### Post by blinkme on 2007-04-19
alt+ctrl+F2 does bring up the terminal window

---

### Post by blinkme on 2007-04-19
not sure how i can fix it once in terminal window though. been playing around with it and no luck

---

