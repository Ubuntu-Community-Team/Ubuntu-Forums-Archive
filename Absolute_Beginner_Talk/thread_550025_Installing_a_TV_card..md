---
title: "Installing a TV card."
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by johnbull on 2007-09-13
I have a Hauppauge WINTV-HVR-1300 TV card that works fine under Vista on my dual-boot setup. 

I'm now trying to run it with MythTV on the Feisty system. When I run MythTV setup I get into problems. I get as far as the Capture Card section when it starts going wrong.
First it correctly identifies the card on the Probed Info line, but wrongly describes it as an Analog TV  device. (In fact, it is Analog/DVB/DAB Radio). If I try to correct the description line it immediately says it can't open the card. If I leave the description as is I get nowhere when it tries to scan for channels.
In fact, I don't get very far with MythTV setup at all.
After lotsa web searching I'm drawing the following conclusions.

1. The card will work under Linux (it says so on the Hauppauge website and it appears most all Hauppauge cards work well.)
2.  The card firmware is bang up-to-date as I downloaded it and installed it under Vista (and it works)
3.  I read on this forum somewhere that the necessary dvb drivers are included in the Ubuntu kernel and thus no further downloads are needed.

Can't find any hints on the MythTV site or on any other HOWTOs - anyone care to help me get this thing going?

---

### Post by tgm4883 on 2007-09-13
Actually, you probably have to modprobe the driver to get it to work.  Try this then try setting it up in mythtv

sudo modprobe cx88-dvb

If that works, then add cx88_dvb to /etc/modules so it will do it at boot, otherwise every time you have to reboot you will need to manually modprobe it.

---

### Post by Maestro23 on 2007-09-13
Here's the Ubuntu MythTV Doc: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

Good luck man.:guitar:

---

### Post by johnbull on 2007-09-13
Thanks for that TGM - it seems to have kicked it into life. (but I'm still struggling)
Someone told me to use Kaffeine as a sure-fire way to test the card is working, but when I launch Kaffeine I get the message "Cant bind info socket"
Is this a clue?

---

