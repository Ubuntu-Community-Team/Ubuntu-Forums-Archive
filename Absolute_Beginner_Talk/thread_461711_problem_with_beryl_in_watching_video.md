---
title: "problem with beryl in watching video"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by weapon-x on 2007-06-02
hi friends i have installed beryl on my PC when i switch to it and try watcha movie on vlc there is no video but i can here the sound ,when i switch back to gnome manger i can watch the movie easily .

please guide me...:D

---

### Post by daimaru on 2007-06-02
what kind of graphics card do you have, what are u running beryl on ? aixgl xgl 
never had this problem but did you try different video players? do they all do the same thing?

---

### Post by weapon-x on 2007-06-02
acc im using on board graphic card. But i also have Nvidia Geforce  XFX Mx 4000 AGP card but when i plug it into AGP slot the system shows me a error during boot up ... thats why i m not using it..

---

### Post by Campingman on 2007-06-02
Hi,
There is a work around to the problems you have with no picture, it works in both Totem and VLC.
For Totem this fix by solicitus works
If you load a terminal and do a;
$ gstreamer-properties
in the Video tab there is a drop down box for Plugin. I had a similar issue and selected "X Window System (No Xv)" and that solved my issue.

For VLC this should do the job
In VLC if you go to settings/preferences/video/output modules click advanced options you can change the video output, I have tried X11 video output and Xvideo extension video output, both now display the video in VLC (a bit choppy though)
[http://ubuntuforums.org/showthread.php?t=415012](http://ubuntuforums.org/showthread.php?t=415012)
[http://ubuntuforums.org/showthread.php?p=2707696#post2707696](http://ubuntuforums.org/showthread.php?p=2707696#post2707696)

---

