---
title: "S-Video to TV"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by rpainter on 2008-03-12
This may be simple, but I have not tried it yet. I have a Dell Latitude D610 laptop, with a lot of AVI movies on it. Rather than having to convert the movies to DVD and burn them, I would like to hook up the laptop to my TV.

The laptop has an S-Video port on the back. I have a cable that goes from the S-Video/Sound on the laptop to the Red/White/Yellow ports on my TV. My question is, do I need to do anything special (other than plug the cable in) to get the picture to show up on the TV instead of the laptop screen?

Like I said, it is probably easy...I just don't know.

---

### Post by herbster on 2008-03-12
Which video card are you using?

---

### Post by forestpixie on 2008-03-12
depends I expect on the grpahic card

with my nvidia - once I'd installed the driver it was a matter of running the settings gui and adding the tv to xorg.conf

---

### Post by rpainter on 2008-03-12
> **herbster said:**
> Which video card are you using?

It is an Intel 915GM Based Video Controller (according to Dell's Site).

I am new to Ubuntu and Linux in general, so I am sorry for the stupid questions...but that is how we learn, right?:confused:

---

### Post by forestpixie on 2008-03-13
There are a few quite old threads about getting tv out working with 915GM - some report success - others don't

[http://www.uboontu.com/results.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=intel+915GM+s-video#1284](http://www.uboontu.com/results.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=intel+915GM+s-video#1284)

---

### Post by reacocard on 2008-03-13
> **forestpixie said:**
> There are a few quite old threads about getting tv out working with 915GM - some report success - others don't

[http://www.uboontu.com/results.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=intel+915GM+s-video#1284](http://www.uboontu.com/results.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=intel+915GM+s-video#1284)

don't use old guides, as of gutsy, xrandr is the way to go. I also have an intel 915 with tv-out, here's the command I run to enable the s-video out:

xrandr --output TV --mode 640x480 --below LVDS

that enables the TV out in extended desktop mode, with the TV screen placed below and towards the left of the internal monitor. You can configure it other ways as well, see 'man xrandr' for details.

---

### Post by forestpixie on 2008-03-13
ther you go then - a new guide 

couldn't find that when I was searching for it yesterday

---

### Post by rpainter on 2008-03-13
> **reacocard said:**
> don't use old guides, as of gutsy, xrandr is the way to go. I also have an intel 915 with tv-out, here's the command I run to enable the s-video out:

xrandr --output TV --mode 640x480 --below LVDS

that enables the TV out in extended desktop mode, with the TV screen placed below and towards the left of the internal monitor. You can configure it other ways as well, see 'man xrandr' for details.

Sorry to be so ignorant, but do I just put that command in the terminal? DO i need to do any configuration to Xorg.conf, or will that command make my TV out work? Thanks for your help.

---

### Post by reacocard on 2008-03-13
> **rpainter said:**
> Sorry to be so ignorant, but do I just put that command in the terminal? DO i need to do any configuration to Xorg.conf, or will that command make my TV out work? Thanks for your help.

yep, just in the terminal, no xorg.conf magic should be needed.

---

### Post by jseiser on 2008-03-13
i got hdmi cables with my geforce 9600, but i dont have a hd tv, as soon as i get one, i want to get my stuff playing on the tv, is the approach the same for an hd set up?

---

### Post by forestpixie on 2008-03-13
no with nvidia you can get the driver installed and then use nvidia-settings

---

