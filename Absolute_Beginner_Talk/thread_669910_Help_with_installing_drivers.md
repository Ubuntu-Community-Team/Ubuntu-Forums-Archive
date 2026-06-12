---
title: "Help with installing drivers"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by spolta on 2008-01-16
So I've installed Ubuntu with dual boot (alongside Vista) on my Toshiba Satellite. As a few of you may know by now, the common wireless card found in Satellites is a Realtek, RTL8187B. After hours of dealing with things that confused me (I'm a Linux noob) I found a patched driver for that wireless card. I now have the patched driver but I have no idea whatsoever on how to install it. I have a bunch of files and I don't know where to begin. Help is greatly appreciated, now that I have Ubuntu, and I love it, it would be PERFECT to be able to wirelessly connect to routers without having to boot up in Vista any time I wanted to surf the net.

---

### Post by spolta on 2008-01-16
Bump, please help.

---

### Post by eolson on 2008-01-16
Have never dealt with the Realtek,   but .....  is there a file in the pile of files with a  .inf extension?

---

### Post by spolta on 2008-01-16
No there is not.

---

### Post by Sef on 2008-01-16
Please don't bump until 24 hours have passed; otherwise, you could get an infraction.

People in the forums are all volunteers, so sometimes it may take a while for your question to get answered.

You could also do a search and see if anyone else has solved your problem.

---

### Post by eolson on 2008-01-16
Ouch.   Have you tried the restricted drivers?

System > Administration > Restricted Drivers

---

### Post by spolta on 2008-01-16
I will try that, but I doubt it's there. This was a patch that I downloaded on my Windows machine, put on my USB drive, then loaded onto Linux. It's nothing more than a bunch of files from a zipped folder. They have names like install, makedrv, and wlan0up. Is there some way I could execute all of them?

---

### Post by eolson on 2008-01-16
Beats me.   All I know is the driver that ndiswrapper wants has a .inf extention.

I'm hoping somebody else comes along.

---

### Post by spolta on 2008-01-16
Well, I know where I can get a Windows driver for it, and I believe that has a .inf file. How would I use ndiswrapper and where would I get it?

---

### Post by bryncoles on 2008-01-17
I'm having the same problem... except i need realtek ptl8180l 802.11b drivers. 

anyway, i found ndswrapper - click applications, add/remove and type in 'windows wireless drivers' there (im assuming you are on ubuntu gutsy...?). 

if it doesnt come right up to install, try system, administration, software sources and add universe and multiverse repositories. 

then when you install ndswrapper it shouold appear in system, admin, windows wireless drivers....

then you should be able to follow on-screen prompts to install the driver. 

thats the stage im stuck at! :-/

oh - and when i type iwconfig, it says i have no wireless extensions!

i started following the instructions found at 

[http://rtl-wifi.sourceforge.net/wiki/Installing#Getting_the_Driver_2](http://rtl-wifi.sourceforge.net/wiki/Installing#Getting_the_Driver_2)

but when i got to 2:2, getting the driver, i just got very, very confused. whoops! 

can somebody provide a more idiot-proof translation please...?

---

