---
title: "3d on Radeon IGP 330M/340M/350M"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by mells on 2006-12-28
Hi guys,

I know there are allot of questions about getting a ATI card ready to use Beryl, but I've worked through several howtos' and even reinstalled the system but have hit a wall.

I have used easyubuntu to update the ATI 3D driver but now I try and check that I have got it works the system crashes and sends me straight to the login screen. (At least it's booting!!)

Any help would be great.. I will post any info up if needed. It's become a personal challenge to get Beryl working again as it did first time by fluke but I had to reinstall (after playing) and now it doesn't ](*,)

---

### Post by asusguy175 on 2007-01-25
this is the video card that my laptop (hp ze5300) has in it, and i had the same thing happen everytime i try to start beryl.... the first time i used it (right after i installed it) it worked great, and everything seemed fine.... however, during my following ubuntu sessions(all of them) i still haven't been able to figure out why it won't run beryl anymore.... any suggestions on where to begin looking for errors?:confused:

---

### Post by roachk71 on 2007-01-26
**The proprietary fglrx driver is intended only for high-end cards**, I'm afraid.

** Beryl also won't work on these portable chipsets** (ATI's FireGL or a high-end NVidia card is required), and compositing is _painfully_ inefficient.

With that in mind (and if you're using Ubuntu or Xubuntu instead of Kubuntu,) I can offer some help.

Note: You will, unfortunately, need to undo the X script changes made to enable Beryl and/or any other composite managers. Otherwise, you'll just keep driving yourself crazy.

First, type this into your command line after logging into a failsafe terminal:

```
sudo nano /etc/X11/xorg.conf
```Find the Device section, and edit it as follows (leave the BusID line as it is, placing the options after):

```

Driver "radeon"
Option "AGPMode"  "4"
Option "RenderAccel" "true"
Option "AccelMethod" "EXA"
Option "EnablePageFlip" "true"
Option "DDCMode"
Option "ColorTiling" "false"
Option "SubPixelOrder" "NONE"

```Use Ctrl-X and save the file, then log out from your session (with exit). Then press Ctrl-Alt-Backspace to restart your X server.

It works great on my Pavilion xt125. You might also want to increase your video memory allocation in the BIOS configuration. On this computer, the default is 32MB; 64MB or better is preferable.

Now, in my experience, you won't get absolutely stellar 3D acceleration, but your screensavers and most 3D applications should work more efficiently. I had Beryl working for a couple of login attempts using the built-in Radeon driver, but got tired of the X crashes. I'll never try it again on this notebook...

---

### Post by asusguy175 on 2007-01-26
i did what you said, and is all it did was make my initial boot time splint in about half.... but when i started beryl, i couldn't see the close button on the windows because usually they're supposed to be slightly see-through and when you close the window it's supposed to have those star things (default theme) but every time, none of that was there.... just blank, and when i moved the window, it bent like it's supposed to, but when i transferred to another desktop, CRASH, and when i closed a window from the desktop open windows bar, (yup, you guessed it) CRASH.... so i got a little P.O.ed after a week of trying different things to get it working, and is all i did is screw myself out of the legit /etc/X11/xorg.conf file...is all i know, is i'll save beryl for my desktop ;(... lemme know how to get my original xorg.conf file back if you can... PLEASE..... this is me, giving up....

---

### Post by roachk71 on 2007-01-26
That's easy:

Just type dpkg-reconfigure -phigh xserver-xorg in a root shell and reboot.

Of course, you have to use a failsafe GNOME session and remove Beryl and Emerald from your startup program list in the session manager after this, or they'll still run at GNOME startup.

Trying Beryl and Emerald on my notebook (this one has an IGP 340M) nearly fried my graphics chip, so I gave up on it as well.

---

### Post by Lord Darth Vader on 2007-02-06
My laptop has 340M and I had the impression that beryl won't work on it. So I was using Ubunto for almost 4 months and the best eye candy I had was xcompmgr. One day I dared to follow the quide on beryl official website and ... It is working happily ever after. Ok, I admit that performance is not that brilliant but it works fine. The only drawback I experience is that scrolling speed is slow (in firefox, pdf reader, ...).

---

### Post by vanlinx on 2007-02-12
Hey,

stuff edgy, 

I went back to Hoary 5.04 and everything works as it should be..What the hecks going on? It's like ATI support has degraded?

Hoary and ATI, work out of the box!!!

---

