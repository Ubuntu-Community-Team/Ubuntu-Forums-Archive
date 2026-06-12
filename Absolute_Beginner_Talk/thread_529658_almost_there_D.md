---
title: "almost there :D"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-08-19
alright... i've been trying to get ubuntu on my moms old computer for the past 3 days, and i just succeeded in installing with no error messages :popcorn:


unfortunately, there is something wrong with the graphics card:

starting ubuntu normally runs the loading screen, then goes to a black screen

running ubuntu in safe mode, then typing startx gives the same result.


how can i reconfigure the graphics card and download drivers from a text based interface?

---

### Post by Hobo Joe on 2007-08-19
Follow all these commands:
```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb

dpkg -i /home/envy_0.9.7-0ubuntu8_all.deb

envy -t

```
The select the appropiate driver and install!

(This will only apply to ATi and nVidia, if you have an intel, there is a different way)

EDIT:

For Intel, run the following command:
```

sudo aptitude install xserver-xorg-video-intel

```

---

### Post by Tyke91 on 2007-08-19
thx, i have an ati card and so the above one should work fine

(btw, i noticed that you had the same problem as me... i dont quite know how i solved it... i just tried installing ALOT of times [hurray patience!])

---

### Post by Hobo Joe on 2007-08-19
> **Tyke91 said:**
> thx, i have an ati card and so the above one should work fine

(btw, i noticed that you had the same problem as me... i dont quite know how i solved it... i just tried installing ALOT of times [hurray patience!])

Well, I'm pretty convinced that in my case it was a bad hard drive. But who knows, maybe I'll try some more.

Glad that you got it though! :)

---

### Post by Tyke91 on 2007-08-19
hmm... envy installed and updated my drivers, but i still have the same issue with the black screen... what now?

---

### Post by Hobo Joe on 2007-08-19
Hmmmm, did you let Envy configure X for you?

---

### Post by Tyke91 on 2007-08-19
i did.... it wouldnt do an automatic ati install, so i did a manual and hit all the defaults (i figured they were the best)

---

### Post by Tyke91 on 2007-08-19
hmm... new effect... no more black screen, but a blue screen telling me that xserver will shut down because it is not configured properly..


how can i configure it properly for an ATI card?

---

