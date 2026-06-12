---
title: "Poor NVidia display after Ubuntu 7.04 install."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by bodean on 2007-04-20
I have a Geforce GO7400 video card.  My resolution options will not let me go any higher than 1024  (I believe I use to run 1280), and my refresh only has an option for 50, which is too low, should be 65.  Not sure why this is. I did install the unrestricted driver package as promped in ubuntu.

---

### Post by rhaaa on 2007-04-20
I have the  exact same problem here, but instead I have an ASUS video card with NVidia GeForce 6200 Turbocache 256mb chipset.

When I ran the live CD, I could use a frequency of 60Hz, but after installing Ubuntu & the unrestricted driver package it lowered to 50 Hz.

Under WinXP on the same workstation I used a 1280 x 1024 resolution at 75Hz.

---

### Post by velkrohed on 2007-04-20
I have an EVGA gforce 8800 gtx, I installed the latest Nvidia Linux drivers from thier site, used the xconfig util they have and it didnt work. I had to manually go into xorg.conf and add the resolutions i wanted in the profiles. 

Another note... if you are going to be installing the nvidia drivers from a clean install, there is a part in the instructions where it tell you to drop to a virtual terminal to stop xserver. When i did I would get a black screen and couldnt get out other than hitting the good ole restart button. I found that before installing the nvidia drivers go into xorg.conf, look for the video card section, and change "vesa" to "nv" and that did the trick for me.

---

### Post by rhaaa on 2007-04-23
I found the xorg.conf file and added the resolution "1280x1024" in each subsections.

After restart I could switch my screen resolution to 1280x1024. However, the refresh frequency is still 50Hz.

I also found out the nvidia driver was installed correctly, as I have been able to enable the desktop effects.

I tried to modify the vertical & horizontal sync. numbers in xorg.conf to enlarge the span to 85Hz but it just completely broke the boot of Ubuntu; my PC booted in command-line mode, no Xwindow for me.

I had to learn VI on the fly (I am grateful I had another computer hooked on the internet in the room) just enough so I could fix the xorg.conf file by removing my modification to the sync numbers.

In summary, out of 3 potential problems I was able to fix 1 with modification to xorg.conf, that another wasn't a problem after all (the driver is installed) and I am still wondering how I'll get my screen to refresh at 75Hz...

Any ideas?

---

### Post by Echo35 on 2007-04-23
I've had this issue too. I can only get my 1440x900 monitor up to 55 MHZ. It used to be 75 in 6.10, and I would like to bump it up to where it was.

---

### Post by dingansich on 2007-04-23
velkrohed: at the blank black screen the OS is still running, it's just that you're just not on a virtual terminal.  You can switch between virtual terminals with the Alt-Left Arrow (or Alt-Right Arrow) key combination.  That should take you to a log in prompt.  No need to hard-restart.   Just in case you find yourself in that position again.

---

### Post by cendant on 2007-04-23
All your troubles are easily solved by playing with automatic tool

sudo dpkg-reconfigure xserver-xorg

It is so easy!

Best regards 
[www.siberian.ws](www.siberian.ws)

---

