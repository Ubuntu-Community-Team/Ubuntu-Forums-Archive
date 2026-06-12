---
title: "Nvidia Graphics Drivers"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-03-21
I'm new to ubuntu but really like it and having just installed it and got it all working on my machine, I need to get the correct display drivers which in my case are NVidia ones. Has anyone done this before and can give me some guidance? My knowledge of ubuntu is not extensive and of linux in general. 640x480 can get really annoying after a while! ;-)    Appreciate any help!

---

### Post by r4ik on 2006-03-21
Here's a little howto.

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

Good luck.

---

### Post by Aewheros on 2006-03-21
Or if you want it to be as easy as possible, let [Automatix]("http://www.ubuntuforums.org/showthread.php?t=138405") install the drivers for you.

But there is nothing wrong with doing it yourself.
Linux users benefit greatly from learning something about how the system works.

---

### Post by tommy1987 on 2006-03-21
Automatix looks good, but it says connection refused when i try and follow the instructions, ahhhh!!! this is getting annoying nothing is working!!!! ;-)

---

### Post by KansasJoe on 2006-03-21
sounds like you have more of a screen problem than a driver problem...do all of the nvidia dl's and such and if that doesn't work you may have to put in a HorizSync and VertRefresh

Go to the monitor section in /etc/X11/xorg.conf and find your monitor section....read your monitors manual or do a google search for your monitors horizontal sync and refresh...mine was also stuck at 640 x 480 until i did this....originally looked like this

Section "Monitor"
Identifier "DELL P780"
Option "DPMS"
EndSection

Changed it to this and now it give me 4 different resolutions and 5 different refresh rates to choose from (your identifier, horizsync and vertrefresh will be different than mine because of monitor)


Section "Monitor"
Identifier "DELL P780"
HorizSync 30-85
VertRefresh 48-120
Option "DPMS"
EndSection

---

### Post by tommy1987 on 2006-03-21
sounds like a plan, well its worth a go i guess...

---

### Post by tommy1987 on 2006-03-21
Just tried it and it works a treat, thank you very much, yet again the Linux community helps me out,,  cheers!

---

