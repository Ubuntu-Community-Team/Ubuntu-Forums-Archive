---
title: "Help? Screen resolution stuck @ 640x480"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by luckylucky on 2006-10-24
Help please...

I am trying to install Ubuntu on a friend's laptop but have a problem... only 640x480 resolution is available but I would like a larger screen (i.e. 1024x768 or 1280x1024).  I've tried installing 915resolution and going into system>preferences>screenresolution but no matter what I do I have only one option, and that is the sucky 640x480.  So far my friend is not impressed, but I really want to wow him with this and appreciate any help to fix this stuck resolution.  Thanks

---

### Post by TitusDalwards on 2006-10-24
by manually you can change /etc/X11/xorg.conf file.

SubSection "Display"
Depth 1
Modes "640x480"
EndSubSection

in this section you can change the resolution type instead of 640x480

---

### Post by ReaderRat on 2006-10-24
Run this code:
```
sudo dpkg-reconfigure xserver-xorg
```
and go through the setup and pick the resolutions you want available Do not pick any that the display can't handle (Check the Owner's Manual)

---

### Post by brentoboy on 2006-10-24
if you dont know exactly what chipset the graphics card is for the laptop, select VESA when dpkg-reconfigure xserver-xorg asks you what video driver to support.

VESA works in most cases, but doesnt use accelerated 3D stuff.

Chances are you have an ATI mobility chipset of one generation or another.  If so, the ATI driver might give you better results.  It is also likely that the Ubuntu installer thought you had an ATI chip and tried to use that driver, and that is your problem in the first place.

if you look up the laptop model on line, you can probably determine the graphics card chipset (as well as other chip sets) by looking for the windows XP driver for the laptop.  even though the driver wont help you, often times, it will tell you what chipset it is for...

---

### Post by Shadoweater12081980 on 2007-05-30
If you boot to single user mode (ESC at boot, then select recovery mode)
you can do:

# sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
# sudo restart X

I've read that the config file is recreated. I'd read about it first though, I've just come across this

What should work is the old chestnut (from your normal desktop)

#sudo dpkg-reconfigure xserver-xorg

most of the defaults are ok but add the resolutions need adding when you get to the display section

I've used it before with my Nvidia card and it worked ok but had to revert to an old xorg.conf when i got a bit too enthusiastic

ALWAYS BACKUP THE OLD XORG.CONF!!!!!!!

---

