---
title: "Monitor Configuration"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by ahaider on 2008-04-11
I have recently installed kubuntu. it installed correctly but there was a problem with display resolution. The resolution picked up was 800x600 and then after a reboot it was 640x480. 
In an effort to correct the resolution, I changed the monitor configuration from "Plug-N-Play" to "Monitor-1280x768". It prompted me to log-out and restart the x-server. I did so with the result that display went out completely .

Can I set the monitor configuration back to "plug-N-play" through 'Recovery Mode' (console) ? Bcoz currently there is no graphical display visible.

---

### Post by phidia on 2008-04-11
If you know your video card and monitor specs you can type the following commandl: > sudo dpkg-reconfigure xserver-xorg
That will open a program to configure your graphical interface.
Answer the questions in that program and hopefully  you will have your xserver back.

---

