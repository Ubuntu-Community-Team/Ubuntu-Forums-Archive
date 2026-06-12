---
title: "Black screen instead of login screen"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Jugney on 2007-12-26
Hi all,

Am installing the 32 bit version of Ubuntu again after trying the 64 bit version and I just couldnt' get it to work, despite having dual AMD64 processors. 

And I'm having the same problem as last time - the screen goes blank the computer stops dead when it's supposed to load the login screen. I have an nVidia graphic card and have tried using dpkg-reconfigure xserver-xorg and setting the driver to 'vesa' but it still doesn't work. Perhaps some small setting is off. Please help!

---

### Post by spiderbatdad on 2007-12-26
sometimes this is caused by improper settings in /etc/usplash.conf  Idk if there is a problem with your video driver. if so, there are several for nvidia cards in synaptic.

Try waiting several minutes on black screen...hit esc a few times...see if splash screen eventually comes up.

---

### Post by chebuntu on 2007-12-26
Hi Jugney, 

Same thing happens to me.  Only work-around I've found is to:

1. cold boot pc
2. while pc is still booting hit "ESC" repeatedly until your os boot choices come up 
3. choose the one that says "...recovery" - hit enter
4. this will take you to a command prompt
5. once there type "init 5" (without quotes) and you will then  be taken to the graphical logon screen.

Hope this helps, 

Cheers, 
Che

---

### Post by Jugney on 2007-12-27
Thanks for the feedback.

I got it working (just as I did the last tiem I installed it) just through sheer persistance. Somehow it just worked one time, and I have no idea why. Cranky graphics drivers?

What I actually did, after multpile times going into xserver-xorg and choosing the vesa driver, was to purposely choose a wrong driver (amd) and then come back to the vesa driver.

Oh, and well, I did another thing...I got a really good hug from my friend, which helped my frustration, and then told Ubuntu "I love you" as it was booting up.

---

### Post by spiderbatdad on 2007-12-27
wondering if you ever looked at /etc/usplash.conf to see if the values were consistent with your supported screen resolution?

---

### Post by Jugney on 2007-12-27
I just checked, and it was correct - 1280 x 800. I seem to remember this is what I did both this time and last time that allowed the system to remember the resolution correctly instead of always reverting back to 800 x 600 : 

System - Preferences - Screen Resolution and checking the box for setting this as the default resolution for ubuntu (I don't see why it wouldn't be set as the default anyway if I had specified it under Screens and Graphics. But I understand that feature is new to Ubuntu, so I'll give em some leeway ;)

---

