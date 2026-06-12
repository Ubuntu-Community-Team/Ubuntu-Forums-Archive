---
title: "don't let my alias fool you...i'm just a noob"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by bigfatmonster on 2007-04-16
Hi, in short i'm a noob at linux. want to leave windows and well ubuntu looks amazing with beryl. so that's what i want to use.
i installed ubuntu and installed the drivers for my video card which is working.

i have an ATI radeon 9550. my primary monitor is a 19" LCD and works fine, but
the problem is that i want to use a dual screen configuration where, my main monitor is in DVI and i have plugged in a projector in the VGA plug. which finally i was able to enable by adding and running the ati config enable command.
===== in the device section
Option "DesktopSetup"  "horizontal" #Enable Big Desktop
Option "Mode2"         "1280x768" #Resolution for second monitor
Option "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO
Option "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
Option "HSync2" "65" #This sets the horizontal sync for the secondary display. 
Option "VRefresh2" "60" #This sets the refresh rate of the secondary display.
===================
then i went to check my xorg.conf file and it added my 2nd monitor(projector) and a whole bunch of stuff 

so i see a signal, the problems lies that the image is not good, every 3rd or 4th pixel is shifted to the right so it gives me a pixelized blurry image, but i can kind of distinguish that it's outputing a clone of my screen.

my 2nd problem, is that i installed beryl and everything is great, except that it won't run because of some error...but i want to fix 1 problem at a time..so i'll get into it afterwards...if anyone can point out a good place to help me configure my video card, it would be great...
also, is it always this hard to configure something in linux?
how would i know the syntax of xorg.conf...is there a place where i can learn the coding for it.
thanks.

---

### Post by freebeer on 2007-04-16
> **bigfatmonster said:**
> 
also, is it always this hard to configure something in linux?


Generally speaking, no.  What you're trying to accomplish sounds like "advanced" to me.  I **think** that beryl is still in it's beta stages (I haven't tried to use it, myself, so I have no first-hand knowledge.)  Then you're trying to deal with a second output on top of it.  Sounds like "leading edge" if you ask me.  But I tend to stick to the safer side of computing.  :D

It's very possible that what you're trying to do **is** possible, but I don't know what the solution might be.

Sorry that I can't help you with your particular problem.  I didn't want you to think that all issues with Ubuntu are difficult.

---

### Post by bobplano on 2007-04-16
beryl is beta software so if you are really new to linux you might want to hold off on getting that for a bit. to run beryl on ATI cards you need to make sure you have fglrx drivers and make sure they are set in your xorg.conf. look for something like drivers "ati" and change that to fglrx once you have them. this *might* solve your problem with the other screen but i doubt it. also if the new drivers are already there or they don't fix beryl can you please post the error here

---

