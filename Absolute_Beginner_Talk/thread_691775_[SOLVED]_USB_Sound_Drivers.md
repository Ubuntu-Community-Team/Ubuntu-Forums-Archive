---
title: "[SOLVED] USB Sound Drivers"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Yudraciell on 2008-02-09
ok heres the story i have the ubuntu 7.10 flavor of linux and i cant get my audio drivers to work (i have been looking for 8 hours now) so i was wondering if someone could be nice enough to help me out.

My computer is set up abnormally seeing as my HD surround sound stereo system is hooked up via usb 2.0, i am using this codec:

ALC888

and my usb setup (saw this in another post)

kaito@kaito-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 010: ID 045e:00e1 Microsoft Corp. 
Bus 001 Device 007: ID 08bb:2704 Texas Instruments Japan 
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0b38:0003 

and thats all i could think of to help u help me :(

if anyone can help me i would be really grateful

---

### Post by spiderbatdad on 2008-02-09
maybe this will help:[http://alsa.opensrc.org/index.php/Usb-audio](http://alsa.opensrc.org/index.php/Usb-audio)

---

### Post by Yudraciell on 2008-02-09
nope didn't help

i found out that it doesn't work on the internet (Firefox) so i cant watch youtube or veoh :(

---

### Post by dragonneus on 2008-02-14
I have the same issue. Im using a usb sound device for audio and it works except for on the internet (with browser) or the system sounds.

---

### Post by paydaydaddy on 2008-02-14
I can't tell from the info you gave if you have whether you have no sound at all, or if it is just no sound via usb. Have you checked all settings in alsamixer? Check out this link if you are getting no sound at all. [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)
Youtube requires a flash plugin. Just tossin' out a few ideas.

---

### Post by Yudraciell on 2008-02-19
Yes it worked with a clean install when everything was plugged in

---

