---
title: "Avoid restarting X"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Kiri on 2008-03-25
It seems like it is necessary to restart X (ctrl alt backspace) after doing a lot of basic changes in linux. It is fairly quick to do so, but the inconvenience is that all the running apps get closed and must be restarted after logging back in. 
Is there away to avoid having to restart X and re-open all the apps everytime?

---

### Post by hyper_ch on 2008-03-25
x needs only retarted if you do something to it (e.g. install compiz or altering your video drivers)...

You can save a session so upon the next start it will auto-start all your open applications that you had before the xserver restart.

---

### Post by kellemes on 2008-03-25
> **hyper_ch said:**
> x needs only retarted if you do something to it (e.g. install compiz or altering your video drivers)...

Indeed.

@OP: I wonder what basic changes you mean..

---

### Post by Kiri on 2008-03-25
> **kellemes said:**
> Indeed.

@OP: I wonder what basic changes you mean..


Well I'm very new to linux, but when I try to follow some guides to get drivers working, or change font settings, etc, they almost always tell me to restart X. I just feel like I have to do it a lot...

But thanks to hyper_ch 's suggestion, I looked at the sessions preferences and noticed I can automatically have it remember which apps I had open and reopen them. Thats cool! :)
I'm going to try it. Thanks

---

### Post by hyper_ch on 2008-03-25
in windows you'd have to reboot the whole OS when you do such changes... in linux you only have to reboot xserver ;)

---

