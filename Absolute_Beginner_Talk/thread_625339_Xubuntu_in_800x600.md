---
title: "Xubuntu in 800x600"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by doorknob60 on 2007-11-27
This is really annoying, I installed Xubuntu on an old computer with a crappy monitor that only works in 800x600, and all the windows are too big! YOu can't see the OK buttons and stuff for a lot of windows. Is there a way to make it better?

PS: Using windows, sometimes I can get 1024x768 to work, but I thik it either needs a special driver or special configuration. So do you have any tips on making 1024x768 to work? Maybbe it needs a lower refresh rater, but I tried the dpkg-reconfigure for it and set it for 60hz (the lowest it would let me) and didn't work...is there a way to make the refresh rate even lower?

---

### Post by doorknob60 on 2007-11-27
COme on people! I know you know this!

---

### Post by schauerlich on 2007-11-27
What kind of video card do you have? Also, there should be a control panel for screen resolution that's separate from the drivers. I'm not sure where it is in xfce. Try that.

---

### Post by doorknob60 on 2007-11-27
It's an old nVidia, Riva TNT or something like that, and whenever i try to change to 1024x768, even at the lowest refresh rater (that it will let me do from the GUI), it shows up all messed up and unusable. What I need help with is to lower the refresh rate lower than 60hz, which might fix my problem. I know I need to edit something in /etc/X11/xorg.conf, but I have no clue what to change...

---

### Post by schauerlich on 2007-11-27
Try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and selecting the nv driver.

---

### Post by doorknob60 on 2007-11-27
I'll try that soon, but I'm pretty sure that driver is already selected, worth a shot though!

---

### Post by -grubby on 2007-11-27
bad idea, as if 60HZ isn't hard enough on your eyes, something lower will kill you (in the eyes)

---

### Post by doorknob60 on 2007-11-27
Hey! Sweet! I don't know what the -phigh did, but it worked like a charm! It didn't ask me to choose the driver, but i chose 1024x768 and worked great. For some reason it never worked when I configured it without -phigh and the livecd didn't even work so I was forced to download the alternate cd. Thank you!!

---

### Post by schauerlich on 2007-11-27
Putting the -phigh option basically skips a bunch of the options that most people don't need to configure and gets straight to resolution/drivers.

---

### Post by burt_57 on 2007-11-28
> **EDavidBurg said:**
> Try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and selecting the nv driver.

robert@robert-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for robert:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071128114259
Te refresh rate for my Phillips 17'' mLCD monitor must run at 60 hrz,,, but I can only run at 51 ?
How can I change the refresh rate ?:confused:

---

### Post by gustasonfrever on 2007-11-28
I'm having the same problem in that I cannot access the OK buttons on windows. I tried typing in that code and it brought up a page where I need to select a driver for the xserver. I have a lenovo t61 and I'm wondering what driver should I use? How do I figure out what graphics card I have?

---

### Post by gustasonfrever on 2007-11-28
ubuntu@ubuntu:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071128124109

I'm getting this after I try and select a driver. What am I doing wrong?

---

### Post by CatKiller on 2007-11-28
> **burt_57 said:**
> robert@robert-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for robert:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071128114259
Te refresh rate for my Phillips 17'' mLCD monitor must run at 60 hrz,,, but I can only run at 51 ?
How can I change the refresh rate ?:confused:

Refresh rate is pretty meaningless with an LCD. Compiz ("Desktop Effects") reports refresh rates in the low 50s even when the refresh rate is actually higher.

> **gustasonfrever said:**
> ubuntu@ubuntu:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071128124109

I'm getting this after I try and select a driver. What am I doing wrong?

Nothing, necessarily. It's just telling you that it automatically made a backup, and named it based on the date.

> **gustasonfrever said:**
> I'm having the same problem in that I cannot access the OK buttons on windows. I tried typing in that code and it brought up a page where I need to select a driver for the xserver. I have a lenovo t61 and I'm wondering what driver should I use? How do I figure out what graphics card I have?

It's either Intel or NVidia, depending on what you chose, according to [this page]("http://shop.lenovo.com/SEUILibrary/controller/e/na/LenovoPortal/en_US/special-offers.workflow:ShowPromo?LandingPage=/All/US/Sitelets/ThinkPad-T-Series/tech-specs").

---

### Post by gustasonfrever on 2007-11-28
Now that I've actually installed xubuntu i'm getting a different response from the terminal 

gustason@gustason-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
Password:

And I cannot type except to hit enter which doesn't let me get any further

---

### Post by CatKiller on 2007-11-28
It's asking for your password. It doesn't display as you type so that people looking over your shoulder don't know how many letters your password has.

---

