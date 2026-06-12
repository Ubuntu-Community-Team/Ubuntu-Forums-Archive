---
title: "Bad video quality"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by firetree on 2007-02-06
While watching some videos, i noticed that quality of videos are worse than windows. I think there is a mistake on my configuration. I was using 32 bit color in windows. I am not sure it is configured as 32 bit now. Could you guess anything to improve?

---

### Post by renzokuken on 2007-02-06
do you have a grafix card? if so you should install the appropriate nvidia or ATI (fglrx) drivers.

there are some great howtos for this in the forums or see [www.albertomilone.com/guides.html](www.albertomilone.com/guides.html)

---

### Post by firetree on 2007-02-06
how can i check if all of the drivers are installed correctly?

---

### Post by dr_d on 2007-02-06
yes i found video quality improved hugely after enabling hardware acceleration.

---

### Post by firetree on 2007-02-06
it seems my hardware acceleration is enabled. 
"glxinfo |grep rendering" gives a yes.

---

### Post by firetree on 2007-02-06
i have a Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller. Am I required to install a driver for it?

---

### Post by Spr0k3t on 2007-02-06
Check to see if you have 915resolution installed.  This should be the driver you need to enable hardware accel.

---

### Post by slimdog360 on 2007-02-06
I dont think so, try installing vlc to play your movies. And some extra codecs from automatix or where ever.

---

### Post by firetree on 2007-02-06
I am using vlc now, i have asked according to quality on vlc. I have also downloaded some codecs, I am also downloading some extra codecs by automatix.

---

### Post by firetree on 2007-02-06
I think now it's good, i have downloaded media players, mplayer and codecs sections. Now gxine and totem plays good, but vlc plays bad. So i guess solution has nothing to do with graphic card. Thank you everyone who tried to help.

---

