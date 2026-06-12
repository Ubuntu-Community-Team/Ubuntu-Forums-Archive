---
title: "Oh Woe is Me!"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by djen9999 on 2007-02-18
Everything was going along fine except scrolling was ragged and jerky.  I was able to change the video driver which smoothed out the scrolling but then I couldn't get the proper resolution on my monitor. I thought I had things straightened out.  That's when it all came crashing down on me.  I restarted the computer and now I can't get past the log in screen.  :( 

I tried the restore mode but I have no idea how to use it.

Have I completely messed things up?

---

### Post by Zuuswa on 2007-02-18
When you are at the login screen, hit control+alt+F1 to get to a terminal.  Then type in the code 
```
sudo dpkg-reconfigure xserver-xorg
```
and answer the questions.  Afterwards, type in 
```
startx
```
or
```
gdm
```
to get back to the login screen.

---

### Post by r4ik on 2007-02-18
Log in with passwrd and username (Ctrl+Alt+F1 if needed to get a CLI )

sudo dpkg-reconfigure xserver-xorg

follow the defaults and finish with a

sudo etc/init.d/gdm restart

If you have a visual get you're drivers here,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

Oke i'll rest my case :)

---

### Post by bulldog on 2007-02-18
Maybe you just have to alter your xorg.conf.
```
sudo nano /etc/X11/xorg.conf
``` and see if your driver is properly displayed.
You can also look if the desired resolution is displayed and if not,add it manually.

---

### Post by djen9999 on 2007-02-18
I get a response xserver- xorg does not exist.

I apparently really screwed things up.

I don't think I mentioned that I log in, the screen goes black then comes right back to the log in page.  don't know if that helps.

---

### Post by bulldog on 2007-02-18
Copy and paste the command exactly as it is,if you make a mistake with a space it won't work.
```
sudo dpkg-reconfigure -phigh  xserver-xorg
``` and set the desired resolution with your space key.
Also take a look at your xorg.conf to see if the driver is enabled!!
See my previous post how to do that.

---

### Post by djen9999 on 2007-02-18
OK.  Remember, I'm a complete newbie here.  How do I paste when I'm in the terminal?  The mouse doesn't function and there's no tool bar to click on.

---

### Post by djen9999 on 2007-02-18
Also, getting the resolution fixed isn't my main concern right now.  I want to be able to get past the log in screen.

---

### Post by bulldog on 2007-02-18
Being a newbe isn't a strong excuse.
You have to take a good look at the commands and type it exactly as it is written.
To be able to login again you have to reconfigure the hardware and that's what we are trying to do here.

---

### Post by djen9999 on 2007-02-18
Well, things are totally messed up now.  I went through and accepted the defaults.  When it got to image depth the default was 24.  I got the following:

xserver-xorg postinst warning: Overwriting possibly customised configuration file; backup in/etc/x11/xorg.conf.20070218131804.

Now I don't even get the log in screen but a warning that I changed the output.  All I did was accept the defaults.

I have come to believe that I have gotten myself in way over my head.  How do I go about getting my partition back and working with just XP?

---

### Post by r4ik on 2007-02-18
go into recovery mode from the XP CD. (it's a DOS prompt)
type
Code:

FIXMBR

It will ask if you are sure. If you are sure, let it do its thing. then type
Code:

exit

and you will reboot into Windows

Good luck !

---

### Post by bulldog on 2007-02-18
> **djen9999 said:**
> Well, things are totally messed up now.  I went through and accepted the defaults.  When it got to image depth the default was 24.  I got the following:

xserver-xorg postinst warning: Overwriting possibly customised configuration file; backup in/etc/x11/xorg.conf.20070218131804.

Now I don't even get the log in screen but a warning that I changed the output.  All I did was accept the defaults.

I have come to believe that I have gotten myself in way over my head.  How do I go about getting my partition back and working with just XP?
It makes only a copy of your old xorg.conf nothing more.
Just reboot and see if there's something changed.

---

### Post by djen9999 on 2007-02-18
All is well.  Thanks.

Next question:  I got my resolution back but scrolling is jerky.  Same with moving windows.  Everything else seems to be working just fine.

---

### Post by r4ik on 2007-02-19
Video driver ?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) (For Ati and Nvidia)

---

### Post by djen9999 on 2007-02-20
You guys are fantastic!  I downloaded tseliots instructions for installing the NVIDIA drive and everything is working perfectly.  I must admit that I approached things with some trepidation, but following the instructions step by step got me through.  Thanks again.

---

