---
title: "screen resolution"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by musicphotog on 2007-07-24
first of all let me say that i am a complete n00b. sick of windows and bored with osX, i have installed ubuntu on one of my machines. this is an older dell optiplex GX260. with the onboard graphics card i could not increase the resolution above the 800x600. Figuring out the install was fun as i couldn't see the bottom of the window, but hitting enter seemed to solve the issue. i was hoping it would have been resolved with some updates, but i was still stuck at the low rez even after the full install. so i dug up an old dual monitor agp video card and plugged it. i had to reinstall the OS, but it works much better. the issue i have now is that i am not able to adjust the screen resolution to the optimal 1680x1050 for my dell 20" widescreen. i do not even know what kind of video card i have in there, but i'm sure i can figure that out. 
so my questions are, do i have to know exactly what video card i have before i can make this update, and how can i get to optimal resolution? 

thanks in advance. [IMG]http://musicphotog.com/temp/cheers.gif[/IMG]

---

### Post by benx009 on 2007-07-24
yes, you would want to know what type of video card you are using.  installing the proper drivers for your video card should allow you to use higher resolutions w/o any problems.

btw, what version of ubuntu are you using?

---

### Post by namich on 2007-07-24
Have you tried the  : SYSTEMS > PREFERENCES > SCREEN RESOLUTION  option.

---

### Post by musicphotog on 2007-07-24
> **benx009 said:**
> yes, you would want to know what type of video card you are using.  installing the proper drivers for your video card should allow you to use higher resolutions w/o any problems.

btw, what version of ubuntu are you using?

ok, so when i figure out which video card it is, how hard will it be to install the correct drivers? the reason i put this card in as opposed to the onboard one that would only give me 800x600 is because the driver update seemed pretty involved

and i'm pretty sure i'm running 7.04. i'll have to verify when i get home though.

> **namich said:**
> Have you tried the  : SYSTEMS > PREFERENCES > SCREEN RESOLUTION  option.

yes; the option i want is not listed.

---

### Post by phr0ze on 2007-07-24
You don't need to know your video card.

Type or copy the following into a command line assuming you are using Ubuntu and not kubuntu, etc.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bak

gksudo gedit /etc/X11/xorg.conf

Edit this file. In the monitor section near the bottom you will see Vertrefresh and Horizsync. Update these values to the ones provided by the monitor spec sheet.

Then in the Screen section go down to the display section for 24bit depth and add the resolutions you would like in front. Such as
Modes "1680x1050" "1024x768" "800x600"

You can edit the other depth sections too but it is unlikely you will run at less than 24bit.

Save the file and reboot.

---

### Post by asmoore82 on 2007-07-24
> **phr0ze said:**
> Save the file and reboot.

save the file and logout... then [Ctrl]+[Alt]+[Backspace] at the login screen

---

### Post by phr0ze on 2007-07-24
> **asmoore82 said:**
> save the file and logout... then [Ctrl]+[Alt]+[Backspace] at the login screen

Same difference. You could also recommend vi or nano as an editor instead too. I prefer the reboot over control alt backspace.

---

### Post by musicphotog on 2007-07-26
thank you very much for the info. i will try this when i get home.

---

### Post by jsr on 2007-07-26
> **musicphotog said:**
> . i do not even know what kind of video card i have in there, but i'm sure i can figure that out. 
so my questions are, do i have to know exactly what video card i have before i can make this update, and how can i get to optimal resolution? 

thanks in advance. [IMG]http://musicphotog.com/temp/cheers.gif[/IMG]

To start with.. find out what display card are you using! 

$lspci

and see the line starting with VGA, that line will tell you the video card that is on the system

---

