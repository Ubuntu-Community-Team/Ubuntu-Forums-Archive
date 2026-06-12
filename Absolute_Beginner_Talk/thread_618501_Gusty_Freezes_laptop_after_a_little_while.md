---
title: "Gusty Freezes laptop after a little while"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by championboxes on 2007-11-20
I am having a problem with Gusty... after I leave it on for a while it will freeze... it freezes everything I cant even see the light come on when i press Caps Lock... I didnt have this problem with fiesty and i have taken gusty off and reinstalled it and it still does it... does anybody have a solution to this? My laptop is a alienware m9700... 

also when i try to install the build-essential it tells me i need to have a cd... i put the cd in there but it still tells me to put it in... is there a way i can just make it download off of the internet?

---

### Post by petervk on 2007-11-20
I had a problem with gusty freezing so I disabled the desktop effects and that seemed to help. You could try that.

The cd thing is a pretty easy fix. You just need to comment out the cd line in your sources.list file.

1. Alt F2
2. ```
gksu gedit /etc/apt/sources.list
```
3. place a ```
#
``` before the cd-rom line
4. Run update manager and check for new upgrades
5. Try installing the build essentials package again.

If you run into problems post the contents of the /etc/apt/sources.list file here.

Maybe someone else can help with the freezing problem?

---

### Post by championboxes on 2007-11-27
I tried what was suggested but It still freezes... I kinda think that it might only do it when i try to download something in firefox? the last two times it has froze I started a download and it froze then the next time the download was almost finished then it froze... I dont want to go back to fiesty... in gusty everything seems to work better other than the freezing problem...

---

