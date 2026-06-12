---
title: "Graphics Card Problem"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by jfd on 2007-11-29
I tried to enable desktop effects with a SIS 650/M650, which is relatively un heard of, and I didn't expect it to work.

On the same machine, I have a Nvidia GeForce 2 MX-400, which was not in use. A notification for a driver for that card came up, so I downloaded it and installed it. I had to restart my computer, so when I did this came up:

Your screen and graphics cards could not be detected correctly. To use higher resoloutions, visual effects or multiple screens you have to configure the display yourself.

Now I think it's in 800x600, Whereas before I had it at 1024x768. I've tried to set it back to the 1024x768 resolution but it just won't go.

I then remembered why I was in this situation, and then activated the Nvidia GeForce 2 MX-400 card. I restarted on the SIS 650/M650 card, so that I could fiddle around with the settings. When I test the settings and have the screen plugged into the Nvidia card, it comes up with the grey screen that says 'confirm these settings' or something. So I confirm them and as soon as it goes onto the desktop, i just see loads of funny white lines flashing.

I know this is vague, but could somebody help me?

---

### Post by quandary on 2007-11-29
maybe you have to reconfigure xorg config.

try xorgconfig or xorgcfg. 
The name and path of the X configuration file is /etc/X11/xorg.conf

Be sure to backup the old xorg.conf file before you start messing around with it...

---

### Post by jfd on 2007-11-29
I dunno what to do with that though =/

Grr it's so annoying lol

:confused:

can anyone else help?

---

### Post by quandary on 2007-11-30
> **jfd said:**
> I dunno what to do with that though =/

Grr it's so annoying lol

:confused:

can anyone else help?

on the command line, try this:
dpkg-reconfigure xserver-xorg

backup the config file, as I told you:
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

If you can't do anything anymore, try console login in a virtual terminal:
For that, press: CTRL + ALT + F1

If you wan't to go back to xorg, press: CTRL + ALT + F7

To edit the config file manually, in the console, type: 
sudo nano /etc/X11/xorg.conf
If you just want to look at the xorg.conf, and want to be sure not to change anything, don't use sudo

---

