---
title: "SWEEX webcam &amp; TRUST microphone"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by gganitis on 2007-09-24
Hi there. Sorry but I am a really new ubuntu user, so I have no idea what to do in order my new webcam (sweex) and my new microphone (Trust) to work in ubuntu. 

Reading some threats in this forum, I didn't understand if I have to install driver, application, both, where to find them, and in which way.

[COLOR="Red"]ABOUT THE WEBCAM[/COLOR]

Writing in command: "lsusb", 
I get: 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 005: ID 0bc2:0502 Seagate RSS LLC 
Bus 005 Device 003: ID 0402:5603 ALi Corp. USB 2.0 Q-tec Webcam 300
Bus 005 Device 002: ID 05e3:0608 Genesys Logic, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


[COLOR="Red"]ABOUT THE MICROPHONE[/COLOR]
...when I turn it on, I hear a voice by the speakers but... it doesn't work.
I tried to  change the System/Preferences/Sound standards, and anything was possible in the volume control (OSS and Alsa mixer)

Any information? Please!

Thanks everyone.

---

### Post by linuxwizard on 2007-09-24
Look down this page  
[http://alpha.dyndns.org/ov511/cameras.html](http://alpha.dyndns.org/ov511/cameras.html)
No driver for that unit.

 Sweex  USB 2.0 Webcam 1.3 Megapixel (K00-16620-e05 on cdrom)  	N/A  	ALi M5603    OV7640        No driver yet.

---

### Post by gganitis on 2007-09-25
So, I have to wait to use my webcam...

About the microphone? I forgot to tell you that is connected in "line in" of my sound blaster audigy SE. It's not USB.

Thanks for the information

---

### Post by linuxwizard on 2007-09-25
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by gganitis on 2007-09-27
The first link helped me make my mic to work!!! :)
I couldn't understand that the choice "capture" has to do with microphone.

In the second link, everything is really logical, but in my ubuntu the volume control, has another choices in preferences.

Thanks a lot! :lolflag:

And about the webcam, the only thing I have to do is to wait for drivers?

---

