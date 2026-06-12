---
title: "64bit laptop black screen"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by yahn on 2007-07-25
I installed the 64bit version of 7.04 Ubuntu on my new AMD 64bit Turion processor with an ATI mobility graphics card.  Everything installed fine, but when I try to boot up Ubuntu after I hit enter on the grub screen and I get the message that said the kernel has loaded my screen goes black.  My computer doesn't shut down, but the screen goes black.

Can anyone tell me how to fix this?  I've been trying to figure it out for a month now.  Thank you.

---

### Post by agurk on 2007-07-27
Does its hard disk activity indicator flash, indicating that the system is actually booting? Can you access any of the TTYs? Press <Alt>+<F1>, <F2>..<F6>

---

### Post by tgm4883 on 2007-07-27
> **agurk said:**
> Does its hard disk activity indicator flash, indicating that the system is actually booting? Can you access any of the TTYs? Press <Alt>+<F1>, <F2>..<F6>

wouldn't that be <Ctrl>+<Alt>+<F1>

---

### Post by agurk on 2007-07-27
> **tgm4883 said:**
> wouldn't that be <Ctrl>+<Alt>+<F1>

Indeed it would, thanks.

---

### Post by yahn on 2007-07-28
When I do that it boots up, but it gives me errors that X server isn't installed correctly.  I have an ATI graphics card, could that be the problem?

I don't know how to fix the X server problem, so if anyone could help I would really appreciate it.  Sorry for taking so long to respond.

---

### Post by agurk on 2007-07-28
Ok, that's good news. Try logging in and type **sudo dpkg-reconfigure -phigh xserver-xorg**
A **sudo apt-get update** followed by **sudo apt-get upgrade** can't hurt either.

If it still doesn't work, please let us know the exact wording of the error message.

---

### Post by yahn on 2007-07-28
It didn't work.  This error keeps popping up:
> error microcode "bcm43xx_microcode5.fw" not available or load failed.

This is the error I got from the x server:
> fatal server error no screens found f"

---

### Post by agurk on 2007-07-28
Alright, check out [this](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/107711) bug and try the advice from Steven Dee. The user Maarten Hogendoorn also posts his working xorg.conf file later in that bug for reference.

You'll find your xorg file residing in /etc/X11. To edit this file, log in at the command prompt and type **sudo nano /etc/X11/xorg.conf** ('nano' is the editor). Make sure you type X11 and not x11.

I'll check this thread back tomorrow. Good luck.


Edit: Oh, and the "bcm43xx" is an unrelated error, it has to do with your wireless card. Sorry about your tough start.

---

### Post by russo.mic on 2007-07-29
Give this a shot, As this is what it took to get my ATI to boot properly.

Access a console, and with an internet connection (you've gotten that to work I assume, just plug in a hard line, don't rely on your wireless) type these commands (enter after each line)

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup

sudo apt-get update

sudo apt-get install xorg-driver-fglrx

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv

startx

I don't think just "sudo dpkg-reconfigure -phigh xserver-xorg" will help, as you need to install fglrx (the ati driver).  
Just for your (and anyone else's) info, the first line just backs up your xorg.conf, which is the xserver configuration file, the next 2 lines update apt-get and then install the driver.  aticonfig --initial seeks out your xorg.conf and sets it to use the ati diver, and the overlay type is set by the next line.  startx just starts xserver.  Be aware that the first time you shut down, it'll just bring you to the command line probably, so type sudo shutdown now, or sudo rebbot now, depending on your need.  

Ignore the broadcom thing, it's just trying to install the driver for your wireless adapter, which you'll have to configure once you get in the system.  I will as will check tommorow to see if your okay.  Don't forget to post your results!  good luck

Russo

p.s. if that doesn't work, 

sudo cp /etc/X11/xorg.conf.bkup /etc/X11/xorg.conf
That will undo what we've done.

---

### Post by DiBiddilyBop on 2007-07-30
Russo

I was experiencing the same problem and that fixed it, thanks for the tip.  However, when I try and boot up now, it still gives me the black screen at first.  I have to hit ESC, go into text startup, and then type startx for it to boot properly.  Any ideas how to fix that?  I am brand-newb to Linux.

---

