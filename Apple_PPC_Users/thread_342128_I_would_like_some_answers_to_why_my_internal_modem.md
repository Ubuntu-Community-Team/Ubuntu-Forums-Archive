---
title: "I would like some answers to why my internal modem not being detected"
date: 2007-01-19
forum: Apple PPC Users
---

### Post by linuxppcuser on 2007-01-19
I have posted here 2 days ago about my internal modem problem not being autodetected.
I would like some answers to fix the problem or something answered
In 2005 I had Kubuntu 5.04 installed on my iMac G3, had no problem with the modem being 
autodetected and now I upgraded to Dapper Drake and now the internal modem is not autodetected, what gives. Is there a bug


linuxppcuser

---

### Post by badgerclan on 2007-01-19
It would be nice to know what you have tried to do so far instead of bitching.:-\"  I don't run Kubuntu but Ubuntu does include 'wvdial' so from a terminal window 'whereis wvdial' (w/o quotes). If it's on your system you can try the following to see if the modem is recognized 'wvdialconf'. It should be able to autoconfig the tty, else you'll need to manually do it.  If it does, then go ahead and edit 'wvdial.conf'. You may need to also edit '/etc/resolv.conf'. If your not sure about 'wvdial' go here for more info:[http://www.eskimo.com/support/Linux.html](http://www.eskimo.com/support/Linux.html)

Is PPP installed on your system?
Have you checked any HOWTO's (even at YDL)?
Do you know what 'modem chip' is installed?

---

### Post by linuxppcuser on 2007-01-19
I have tried 
System/Administration/Networking
under that is the Modem connection to autodetect I get
could not find modem device
Tried gnome-pppd could not find modem 
Tried kppp tried all of the devices there still no autodetect
Tried pppconfig it did not find it either
Now tell me why it was detected in Kubuntu 5.04 PPC
not in Dapper Drake now it like I dont have a modem under Dapper Drake
But under Kubuntu 5.06 I do have a modem

linuxppcuser

---

### Post by badgerclan on 2007-01-20
Looking at some older posts about the same subject shows no success: [http://ubuntuforums.org/showthread.php?t=235733](http://ubuntuforums.org/showthread.php?t=235733)

If Ubuntu is no longer supporting that modem chip you may end up compiling a new kernel to get support. Check the following HOWTO for directions to find the chip manufacture. Had to do the same thing with Dapper to get my Zoom USB modem recognized (ttyACM0). Also there seems to be built in (Conexant chipset) support in Edgy if that turns out to be the chipset in your global village modem.
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Goodluck:wink:

---

### Post by zapi on 2007-03-09
the modem chipset in my eMac G4 is a K56flex, "Rockwell". Is that supported by "Conexant " driver? 

If that is right, I don't see the Ubuntu 6.10 recognizing the internal USB modem on my eMac. I can't find the modem using "sudo wvdailconf wvtest"! 

hcfusbmodem under edgy isn't working as well, I think it is because of the build is only supporting x86 ... where is the driver? (-_-)

---

### Post by RHTopics on 2007-03-09
Here is one link on getting the internal modem to work:

[http://www.ubuntuforums.org/showthread.php?t=355205](http://www.ubuntuforums.org/showthread.php?t=355205)

To summarize it, you now need to manually load the kernel module "pmac_zilog", which will give you modem support.

I have an iMac G3 and did the following the command to see if it would work for me.  And it did:

```
sudo modprobe pmac_zilog
```

---

