---
title: "Problem with LiveCD (no GDM)"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by Enigmatic on 2006-06-13
I got myself a new laptop with an X700 graphics card that I'd like to use, but I'm having huge problems with the graphics. 

I tried typing in live-expert and then hitting enter on the startup, but it didn't seem to do anything, where would I enter that in? Since I thought that could help..

I tried the xserver-xorg reconfiguration, but after killing GDM, it failed to bring it back up.

Any ideas? I can't believe that it can run.

---

### Post by Enigmatic on 2006-06-13
What I tried now was editing the xorg.conf file, and I changed the driver from ati to vesa, and saved. But I still couldn't start the X Server (said it was already running, but I had terminated it).

---

### Post by confused57 on 2006-06-13
You could try   Ctrl+Alt+F7
or 
startx   at the prompt

or(I'm not sure with the LiveCD):

sudo /etc/init.d/gdm restart

what about:
sudo /etc/init.d/gdm start

---

### Post by Enigmatic on 2006-06-13
Tried starting Gnome with both gdm restart (that failed) and with startx I got an error about no modes matching modes for my screen, and it also said that a screen was found but it couldn't find a usable config.

---

### Post by confused57 on 2006-06-13
Looks like a lot of people are having problems with your graphics card:

[http://www.ubuntuforums.org/search.php?searchid=6044857](http://www.ubuntuforums.org/search.php?searchid=6044857)

---

### Post by Enigmatic on 2006-06-14
Finally got this working! I had to setup a static IP and install the ATI driver as described in the Ubuntu Wiki. Then I edited xorg.conf to point it to the fglrx driver instead of the ati driver. Then I did telinit 1, followed by telinit 2, and to my amazement GDM came up!

---

