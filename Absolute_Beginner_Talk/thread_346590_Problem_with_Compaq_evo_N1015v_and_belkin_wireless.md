---
title: "Problem with Compaq evo N1015v and belkin wireless plus card."
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by WallRunner on 2007-01-25
[COLOR=DarkGreen][B]Hello, first of all I like to say that I am very happy with ubuntu, except for one little thing:

My belkin wireless plus G card will not turn on, I have tried everything I can find, ndiswrapper, ndisgtk, window wireless drivers, about everything I can find on google, I was going to try a trial of the program that does everything for you (forgot the name), and couldn get terminal to open it, the wireless card configuration setting also disappeared in system--->administration--->networking, and none of the lights on the card are on.

Any ideas?

[/B][/COLOR]

---

### Post by K.Mandla on 2007-01-26
Can you give us the exact model number and version of the card? And is this a laptop? If so, how old a laptop? (Sorry, I don't know the evo line very well.)

---

### Post by WallRunner on 2007-01-26
[COLOR=DarkGreen][B]It&#347; the evil card, Belkin F5D7011, A.K.A. Wireless G plus from belkin.
The computer is a laptop, manufactured in ´02, 1.19 GHZ processor, 256MB RAM (Planning to upgrade), as I said, I have tried NDISWrapper, NDISgtk, driverloader (demo), and everything I can find, still no help. No lights are turned on, on the card,  and  the wireless connection  icon has disappeared from networking.

EDIT: just did lspci -v, told me the card was disabled, how do I enable it?


From,
Chris.
[/B][/COLOR]

---

### Post by K.Mandla on 2007-01-26
It seems it has a Broadcom chipset; what's important at this point is to find out which *version* of the chipset you have. Perhaps you've already done this, but what version of the Broadcom card shows up under *lspci -vvv*?

If it's a 4308, 4309 or 4318, t's possible you'll just need to use the fwcutter method to strip out the firmware from a driver, and set it up manually.

---

### Post by WallRunner on 2007-01-26
[COLOR=DarkGreen][B]It´s a BCM4318, I tried the fwcutter, but since i not fluent in terminal programming, I cannot get it to work. 

Big EDIT: started using ndiswrapper again, got the activity light to come on and it shows up in networking, still not working.

From,
Chris.
[/B][/COLOR]

---

### Post by WallRunner on 2007-01-26
[COLOR=DarkGreen][B]I fixed it, the whole thing was because my computer was set for eth0, when it should have been eth1, I ran NDISwrapper again, reboot and viola! Internet! Only thing is that the lights on the card are backwards (the activity light acts as power light, and the power light acts like activity light)

From,
Chris.
[/B][/COLOR]

---

### Post by Jroller90 on 2007-02-13
i have the same exact card and i have tried many many things as well. I see you have yours fixed but i have not fixed mine. i have tried everything you have except "fwcutter", i'm not sure what it is. I have my windows drivers installed, just the lights on my wireless card don't come on any more. (they did at one point).

please help!

---

