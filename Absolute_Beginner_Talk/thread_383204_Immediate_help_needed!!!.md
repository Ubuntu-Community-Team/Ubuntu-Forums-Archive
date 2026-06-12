---
title: "Immediate help needed!!!"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by tipsqueal on 2007-03-13
So today I got a new 250 gb sata hard drive and i wanted to use it, but I wanted to boot from it. I did a lot of reading and found out that my best bet would be to either image my hard drive and transfer it, or fresh install. I decided to image my hard drive, in order to do this I used Partition Image and an Ubuntu Edgy Eft Live CD.
After I finally figured how to do it properly, and even after fixing some issues (bad blocks, etc) I finally decided to restart and change my boot drive to the SATA. When the boot cd was powering down or whatever it does so it can restart the computer, it ejected the disc, told me to remove it, close the tray and hit enter. I did what it said, only after I hit enter nothing happened. I tried a good ol' ctrl+alt+del which seemed to restart the shutdown sequence including opening the tray and telling me to remove the disc and hit enter. So after 3 or so tries I just hit the reset button on my computer. 
Now here comes the problem. When my computer boots up not much happens. I hit the power button, fans turn on, hard drives start spinning, and nothing else happens. My mobo doesnt show my gfx card bios like it normally does, in fact my monitor doesnt respond at all. I then proceeded to look at the hex debug code on the mobo and it was stuck at FF which is boot. I tried turning it on an off a few times and still nothing happened. I re-seated my gfx card and RAM, I also unplugged both my IDE and SATA drives completely and nothing happened. I plugged both drives back in and nothing happened. 
This is extremely displeasing and really really inconvenient. I'm really mad that this has happened as it just doesn't seem right at all, I just don't seem to understand why this happened. I'm not new to computers this is at least the 3rd I've made and I've been using Linux on it full time for 6 months now. Please someone help.

In case you are wondering what my system is:

EVGA nForce 4
XFX nvidia 7600 GT
1 gb Corsair value select RAM
AMD 3500+ (939)
Antec 400 watt PSU


Any help is greatly appreciated, even if there is no solution other than to buy new parts.

*EDIT: I just tried turning it on again while I was checking the advanced post codes pdf on my manual CD and it is stuck at 26, which is "reserved", I'm not sure if this will help anyone, it's just confusing me more.

---

### Post by kolinab on 2007-03-13
Hey,

Sounds like an annoying problem. I haven't attempted this kind of procedure before, but I have a feeling (maybe this is obvious?) that it has something to the way the image was written to your new drive. I know that there are tricky little things that can go wrong with Master Boot Records and such, and I wonder if writing an image to a new drive preserves the special way the MBR is written. Do you think that could be the problem?

What happens if you plug the Live CD in again - does everything work as normal? If so, I guess you can eliminate hardware problems (other than the HD I guess). 

I know this isn't probably what you want to hear, but what if you did a clean install onto the new drive from the Live CD? I guess that's what you were trying to avoid by transferring your image from the old drive. 

I know there are some special instructions on restoring the MBR here - like when people install windows to another partition and it screws things up - maybe that is an avenue you should explore?

Mostly just thinking out loud - maybe this gives you something to think about.

Good luck!

K

---

### Post by tipsqueal on 2007-03-13
The problem isnt the hard drive at all, or at least I dont think. I cant even get access to my BIOS. The system wont even boot up. I'll try it with the Live CD like you said, just because I'm desperate. Thanks for the help.

*EDIT: I called EVGA tech support, they told me to reset my CMOS, I did that, then my motherboard would get stuck at debug code 7F, which apparently means my Mobo is screwed, they told me to RMA it.

---

### Post by kolinab on 2007-03-13
Sorry if I misread you - I didn't realise you couldn't get to the BIOS.

---

### Post by tipsqueal on 2007-03-13
No problem, I was apparently beyond help since Tech support specifically told me to RMA my motherboard. Thanks anyways.

---

### Post by lamalex on 2007-03-13
yikes!! keep us posted on this, I'm curious as to the outcome. I was thinking about imaging mine soon but maybe I won't!

---

### Post by tipsqueal on 2007-03-13
> **Iamalex said:**
> yikes!! keep us posted on this, I'm curious as to the outcome. I was thinking about imaging mine soon but maybe I won't!

I dont think it happened because I imaged my drive, I'm pretty sure it was unrelated. I asked the Tech support guy and he said he had no idea either. As for imaging, it was a complete hassle. I used Partimage, it works pretty good for making an image, but if your hard drive has bad blocks it just freezes when you're restoring an image, which I ran into 3 times. I would honestly just suggest saving all the data/media you want and then re-installing. I'll keep you posted though.

---

