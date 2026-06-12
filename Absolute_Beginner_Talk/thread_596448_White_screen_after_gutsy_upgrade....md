---
title: "White screen after gutsy upgrade..."
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by bldgengineer on 2007-10-29
So I did a no no and upgraded to gutsy from the upgrade manager without even reading the help guide here first(I figured everything else went great why not?). At first it did the samething that it did when I installed fiesty, which it failed to start X because it didn't recognize my evga 8600GTS's. So I switched the nvidia generic driver back to "nv" in xconfig(I normally have to do this when a new kernal comes and then I'd run envy and everything is fine after that) and rebooted. Now what I get is the Ubuntu loading screen and when its done loading I get a somewhat whitish grey blank screen with a mouse cursor(that I can move around) where the login screen used to be.

Anyone know where I might start to fix this?

---

### Post by DSn0wMan on 2007-10-29
Did you have an SVN version compiz fusion installed before the upgrade?

This caused the white screen for me. You can hit alt+f2 and hunt around your blank white screen until you see the text cursur. Then you can type in "metacity --replace" That will replace compiz with metacity so you can troubleshoot your problem.

---

### Post by bldgengineer on 2007-10-29
no I didn't have compiz installed at all. I tried to keep ubuntu as basic as possible. It was basically used for internet surfing and word processing/spreadsheet documents. Hell, I only use windows to game on :)

---

### Post by DSn0wMan on 2007-10-29
have you tried just using the vesa driver? Thats a safe fallback until you can get the nvidia driver squared away.

---

### Post by bldgengineer on 2007-10-29
no I haven't. what do you put in xconfig for it?

---

### Post by DSn0wMan on 2007-10-29
I beleive the entry is simply vesa. The easiest way to set it up is to backup your xorg.conf and run dpkg-reconfigure xserver-xorg. 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

```
 sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by bldgengineer on 2007-10-29
Thanks a lot snowman I'll give it a try tomorrow

---

