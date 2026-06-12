---
title: "Problem with recordmydesktop - no sound!"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by some_random_noob on 2008-02-18
Does anyone know how to fix this? I've looked all over the place and it seems that there is no straight-forward answer. Has anyone here got it working before? I don't know what sound device to specify.

---

### Post by jan quark on 2008-02-18
cannot tell you exactly where the problem lies

but try the recording appliaction

istanbul

when you can't record with this app with sound we know there is something wrong with your sound configuration

if you can well then there is some conflict with the application you use now

---

### Post by some_random_noob on 2008-02-18
> **jan quark said:**
> cannot tell you exactly where the problem lies

but try the recording appliaction

istanbul

when you can't record with this app with sound we know there is something wrong with your sound configuration

if you can well then there is some conflict with the application you use now

Istanbul doesn't work either - when I stop recording, the tray icon just says "saving to disk" and it stalls. When I make a video in Istanbul WITHOUT sound then it shows the "save file" window after recording :confused:

---

### Post by rye_ on 2008-02-18
I could never get recordmydesktop to enable sound either.

Istanbul however, does record sound .  When  the program crashes showing the disk icon you can retrieve the created vid from /tmp

then kill the istanbul process within system monitor

Not perfect, but it works

Ryan

---

### Post by some_random_noob on 2008-02-18
> **rye_ said:**
> I could never get recordmydesktop to enable sound either.

Istanbul however, does record sound .  When  the program crashes showing the disk icon you can retrieve the created vid from /tmp

then kill the istanbul process within system monitor

Not perfect, but it works

Ryan

Thanks for the tip. I tried doing this but it still doesn't record the sound. I opened up the video file and it crashed at the part where I moved the mouse in Lbreakout2 (Moving the mouse over a menu item makes a click sound). So I still seem to have sound problems. It's something to do with selecting the right mixer to record from.

Maybe I should get version 0.2.2-2. How do I add the hardy repos?

---

### Post by rye_ on 2008-02-19
have a look at your sound options within system=>preferences=>sound

check you have the appropriate input devices selected

---

### Post by philidox on 2008-02-25
Look at this post I fix my issue [http://ubuntuforums.org/showthread.php?p=4405489#post4405489](http://ubuntuforums.org/showthread.php?p=4405489#post4405489)

---

