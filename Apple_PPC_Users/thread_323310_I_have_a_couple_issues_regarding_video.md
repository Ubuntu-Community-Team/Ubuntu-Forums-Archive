---
title: "I have a couple issues regarding video"
date: 2006-12-21
forum: Apple PPC Users
---

### Post by pyrokenx on 2006-12-21
I recently came by a PowerMac G3 300 MHz (White and Blue) unit that had 64 MB of ram in it..  I got a 128 stick and wanted to put it in along with the 64..


First Problem:
Whenever I use more than 128 MB of ram, video when I go into X is very garbled and mixed badly.  I dont know what to do with that, its always when I use more than 128, maybe it isnt detecting properly? would that have an effect on how my video looks?  The same thing happens when I use just one of my *other* sticks, a 256 MB.

I installed Debian first due to these ram constraints (regarding the installer/LiveCD requirements), it has no problems on 128 MB or even 64 MB.  I am unable to try this in Ubuntu unless I install with the server disc (am I right on that?)..  Anyhow, this is why I believe it has to do with the 128 MB threshold.


Second Problem:
On Debian, I cant seem to make X go above 800x600,  I see no reason that should be happening.  But then again my hardware could be limiting me there, the r128 drivers fail to load on debian, I dont expect this question to be answered, but if its a very common problem I figured it cant hurt to float it onto these boards. I expect a high probability of this problem hitting me in my future Ubuntu install.


I appreciate anyone taking the time to read this thread and appreciate any responses, I have had trouble looking for answers on the web.  :)

---

### Post by stream303 on 2006-12-22
I don't own a G3, but I have seen references to G3's in the threads here to some of them having problems when loading DRI in xorg.conf.  Perhaps #comment that out and try again.

First thing I'd do is make a backup copy of your Debian /etc/X11/xorg.conf file since it seems to get you the farthest.

If you can print it or copy it, I'd use that as a reference starting point.

In Debian su to root, and run

dpkg-reconfigure xserver-xorg
and see if  you can reconfigure for the right resolution.

In Ubuntu, you can do the same, but with sudo:

sudo dpkg-reconfigure xserver-xorg

using cues from your Debian's xorg.conf file.

Just some thoughts...

---

### Post by pyrokenx on 2006-12-22
I ordered a new video card for the unit,

I have a feeling the card I have in there now is poorly supported.  I'd want to upgrade it anyhow, its pretty old.

I am getting a Radeon 7500 (PCI), which is well supported by open source drivers.  Lets see if that helps.

---

