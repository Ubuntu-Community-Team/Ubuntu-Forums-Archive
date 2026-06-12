---
title: "Green Video in Gutsy w/ Compiz Fusion"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by AegisTalons on 2007-12-04
I installed all the gstreamer stuff. I have my running Gutsy with Compiz Fusion using an ATI Radeon card in my laptop. 

Any time I play a video (not flash video, but like XVID, DIVX, etc), I get a green screen in both Totem and VLC. Strange thing is that the audio plays fine. 

Any ideas?

---

### Post by daimaru on 2007-12-04
sounds just like his problem (its just pink not green :) )
[http://ubuntuforums.org/showthread.php?p=3893933#post3893933](http://ubuntuforums.org/showthread.php?p=3893933#post3893933)

---

### Post by AegisTalons on 2007-12-04
I have tried rebooting a couple of times, but it doesn't seem to fix it. Any Ideas?

---

### Post by daimaru on 2007-12-04
so you do have the w32codecs installed ? just incase your trying to watch wmv and divx files that use restricted codecs .

---

### Post by AegisTalons on 2007-12-04
Yea, I do. It doesn't matter what video I'm watching, it all shows up as a green video and sound works.

---

### Post by LookTJ on 2007-12-04
change the default color depths in /etc/X11/xorg.conf to 24 if it is 16

---

### Post by AegisTalons on 2007-12-05
So I tried chaning the depth from 16 to 24. Video starting playing, but Compiz Fusion broke down and wasn't working. Any ideas?

---

### Post by LookTJ on 2007-12-06
would be helpful to post your xorg.conf here.

---

