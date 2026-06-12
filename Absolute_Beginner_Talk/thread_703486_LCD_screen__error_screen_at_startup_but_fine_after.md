---
title: "LCD screen : error screen at startup but fine afterwards"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by idy on 2008-02-21
Hello !

I have installed Ubuntu. Everything is fine when using a CRT screen.

However, switching to a LCD screen in 1024x768 resolution, the following is happening in that order :
- blue screen with red square blinking and 'no signal' into it and something like 'v 60 Hz' ;
- then I see the standard BIOS and stuff loading on the black screen ;
- then back to the same blue screen and blinking red square ;
- and finally Ubuntu loading properly and displaying fine (I had configured autologin).

Should I modify Xorg.conf in any way ?
What should I do so as not to have these horrible blue screens ? (The PC is for my grandpa so I do not want him to be confused too much !).

Thx !

---

### Post by stoneybroke on 2008-02-21
Have you got Nvidia installed on your computer? if you have I had the same problem with a LCD screen the only way I got round the problem was to install Ubuntu with a CRT monitor then install the drivers for Nvidia then change monitors back to a LCD one allowing Nvidia to configure the LCD monitor to the right screen resolution.

Hope that helps

---

### Post by idy on 2008-02-21
Thanks for your answer.

Nvidia indeed. I had installed Ubuntu with the CRT screen, but I might have installed the nvidia drivers after having connected the LCD.

I should perhaps connect it back to the CRT and then back again to the LCD screen ? Or uninstall the Nvidia drivers and reinstall them when on the CRT ?

Thx for your help !!

---

### Post by stoneybroke on 2008-02-21
If you have installed the Nvidia drivers now it should all work with a LCD screen at boot up so connect the LCD screen then boot it and it should work if not send another message I'll be about for a few hours yet ok

---

### Post by idy on 2008-02-21
Well I am sure I had installed the nVidia drivers (as I also activated the advanced graphical effects which could not be activated otherwise) - so I still get the same blue screen... weird.

---

### Post by stoneybroke on 2008-02-21
well that is strange when I ran the install CD on a 64bit comp with a LCD screen I knew Ubuntu was there but I couldn't see it after hours of fiddling I put on a CRT monitor and everything worked once Ubuntu was installed with the CRT monitor I then installed Nvidia drivers closed computer down changed monitors and booted up again and it all worked well so if you have done that and are still having problems it could be down to the LCD monitor not being set to the right resolution have you tried that?

---

### Post by idy on 2008-02-21
Thanks for your answer - how could I modify the resolution of the LCD ? Considering it works fine when Ubuntu is up and running, but not at the beginning, I guess I cannot modify the resolution in Ubuntu ? Or should I modify xorg.conf in some way ?

Thx a lot !

---

### Post by stoneybroke on 2008-02-22
Hi sorry it has taken me so long to get back to you, it sounds like your monitor does not have a setup menu or you would have been able to set the resolution in that if it hasn't then you might have to config xorg.conf but I don't know how you would do that sorry.

---

