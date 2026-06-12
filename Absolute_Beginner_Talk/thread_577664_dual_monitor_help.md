---
title: "dual monitor help"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-10-16
Hey guys,

I would like to run a dual monitor setup with Ubuntu 7.04.

My 2 monitors are:
1) 22" ViewSonic VG2230mw widescreen LCD
2) 15" Gateway CRT

I have read about xinerama but cant seem to find out how to install it.  In xinerama's official website, all i can find is documentation and release notes.

Is xinerama the way to go?  Any recomendations?

---

### Post by jrharvey on 2007-10-16
I run dual monitors in 7.04 with the nvidia config TWINVIEW. It actuall works as dual monitors by stretching the desktop's width.

---

### Post by jrharvey on 2007-10-16
Ihavn't tried xinerma though.

---

### Post by twiceasworn on 2007-10-16
Since you have an intel integrated graphics chip, I personally do not know how to set up dual monitor for it (only done it on ATI).  There are tons of guides out there, especially on these forums about getting it running.  Just doing a google search for "dual monitor intel integrated graphics ubuntu"  brought up a few different guides.

---

### Post by jrharvey on 2007-10-16
With an nVidiaGeForce 8600 GTS just download the nvidia drivers and nvidia configuration editor and switch to twin view. To save the twin view, log in as root and then go back to nvidia controls and click on "save to x configuration file"

---

### Post by bodhi.zazen on 2007-10-16
> **jrharvey said:**
> With an nVidiaGeForce 8600 GTS just download the nvidia drivers and nvidia configuration editor and switch to twin view. To save the twin view, log in as root and then go back to nvidia controls and click on "save to x configuration file"

LOL

No need to log in as root

```
gksu nvidia-settings
```

---

### Post by jrharvey on 2007-10-16
Well I tried that last time but It would not let me save my settings unless I logged in as root. Every time I restarted my computer I had to reconfigure my nvidia settings. I am sure you are right with what you said but that is how I got it to work.

---

### Post by jrharvey on 2007-10-16
I think when i did it I used sudo nvidia-settings. For some reason that doesnt work to save the file but gksu does. Im not sure why.

---

