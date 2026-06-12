---
title: "screen size"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by feed the bear on 2007-04-17
I am trying to install ubuntu 6.10 on an old Dell Inspiron Laptop.  Following instalation there was a graphics problem which I was able to fix by using xserver and selecting vesa.  However, the result was the ubuntu desktop appearing in only the middle of the screen.  I went back into xserver in and changed the resolution to 1400 x 1050 and this meant the desktop almost filled the screen however the login screen will not let me in and just keeps asking over and over for the username and password...

I'd be really grateful for anyone who could offer me any advice.

Mark

---

### Post by zvacet on 2007-04-17
If you tell wich graphic card you use it will be easyer to help you.

---

### Post by Pikestaff on 2007-04-17
Sounds like a driver problem to me, I'm not sure what graphics card you're using but if it's Nvidia you may want to try using the nv or nvidia driver instead of vesa... vesa has always given me problems.

---

### Post by NESFreak on 2007-04-17
the correct resolution for your screen would probably be 1440x900.
I wouldn't know why you can't log in. Does it spits out any error message like thing?
tried ```
sudo dpkg-reconfigure xserver-xorg
``` from the commandline?

good luck

NESFreak

---

### Post by feed the bear on 2007-04-17
According to Ubuntu device manager it is Rage Mobility M3 AGP 2x

---

### Post by feed the bear on 2007-04-17
I also get the message cpufreq: change failed with new_state 1 and result 0

---

