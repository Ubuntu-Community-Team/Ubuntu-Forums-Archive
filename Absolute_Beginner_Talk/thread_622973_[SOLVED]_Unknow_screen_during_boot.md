---
title: "[SOLVED] Unknow screen during boot"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Dragons World on 2007-11-25
I will try and explain this the best I can. When I boot up I get the usplash screen then a orange blank screen then logon screen then orange blank screen then splash screen with orange background then orange blank screen and then the wallpaper. I don't know what that orange blank screen is. I have the restricted drivers enabled for my Nvidia card but don't see the splash screen for it during boot. I thought one of those orange screens might be it attempting to display the Nvidia logo. Any ideas. Thanks

---

### Post by christina_svats on 2007-11-25
I think it's nothing to worry about. I get these screens all the time, and I just guessed they are default screens on Ubuntu. I use ATI Radeon 9700 without the restricted drivers. Anyway, i don't know much, but I wouldn't worry.

---

### Post by Dragons World on 2007-11-25
I wanted to change it to black instead of that yucky orange but don't know where to find it to change it.

---

### Post by jordanmthomas on 2007-11-25
look in system --> administration --> login window.

Somewhere in there you'll see the nasty orange color.  You can click it to change it.

---

### Post by Partyboi2 on 2007-11-25
Does this work?
```
gksudo gedit /etc/gdm/PreSession/Default
```Look for:
BACKCOLOR="#DAB082"

And change, DAB082 to black background:
BACKCOLOR="#000000"

Save, and restart

---

### Post by Dragons World on 2007-11-26
Thank You Partyboi2 that did it. Now the splash screen comes up with a black background. Perfect!

---

