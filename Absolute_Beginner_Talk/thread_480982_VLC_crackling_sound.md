---
title: "VLC crackling sound"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by mlucian72 on 2007-06-22
I have this crackling sound whenever I use VLC. I have VLC 0.8.6 with Ubuntu Feisty.
I've tried to chane the output plugin to OSS in VLC under "sound" and "advanced" but I can't find it.
 Does anyone know how to fix this problem?
 XMMS and all other players work fine, no crackling sound...just VLC.

 Thanks

---

### Post by Inxsible on 2007-06-22
Open up VLC. Click Settings --> Preferences.

1) Expand the Audio tab and then click on Output modules. 
2) Next enable Advanced Options at the bottom right corner of that application window. 
3) Change the Audio ouput module from Alsa audio output to Linux OSS audio output. 
4) Save and restart VLC.

No more crackling sound in VLC :)

---

### Post by mlucian72 on 2007-06-22
It worked. Thanks a lot!!!
Why is this problem caused by VLC?
Is there a way to fix the ALSA plug in?
 Just curious...

---

### Post by Inxsible on 2007-06-22
Glad to have helped. 

For some reason, the Alsa driver for VLC is broke :(

---

### Post by mlucian72 on 2007-06-22
I see...I hope they'll fix it.
Thanks again for the help.

---

