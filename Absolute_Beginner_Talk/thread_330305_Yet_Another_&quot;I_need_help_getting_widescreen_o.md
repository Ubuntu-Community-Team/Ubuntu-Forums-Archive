---
title: "Yet Another &quot;I need help getting widescreen on my laptop&quot; post"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by FingerPie on 2007-01-02
I have looked through roughly 15 posts from people trying to get widescreen resolutions displayed under System>Preferences>Screen Resolution.   As with so many others here, I have the same problems, I can't do it.

As i understand it, i can manually add a desired resolution in place of an unwanted one in xorg.conf... this didn't work (it was listed in the xorg.conf, but still didn't show up in the menu).

I also found that i can run "sudo dpkg-reconfigure -phigh xserver-xorg".  This launches a cheezy ASCII menu system, in which i picked i810 (I have an Intel 915GM in my laptop).

I then get brought to a "resolution selection screen"  I made an asterisk appear in front of 1280 X 800 by hitting the spacebar, then, getting forward is a mystery (there are no instructions  for the crappy GUI).  So I hit "ENTER".  and get this:

xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070102232038

relaunching X after this doesn't show the 1280X800 i need.  

Why do so many people have this problem?  dunno.

I also downloaded the latest driver from Intel, but i have no idea how or where to compile it (so that it is listed in the menu of the reconfiguration program.

Any guesses?

-FP

---

### Post by Denn1s on 2007-01-02
try installing the 915 resolution package from synaptics, it helped for me, i have the same card

---

### Post by MkfIbK7a on 2007-01-02
somwhere in that "crappy GUI menu" it asks you to choose simple medium or advanced choose simple and choose what size screen you have and a suggestion

use
sudo dpkg-reconfigure xserver-xorg 
no -phigh

---

### Post by oilchangeguy on 2007-01-02
i've got ubuntu 6.06 on my laptop and the max shown res. is 1024x768. and i've got a desktop running xandros 3.0 oce linux that runs a 19in widescreen at 1440x900 out of the box with still higher res. listed.

---

