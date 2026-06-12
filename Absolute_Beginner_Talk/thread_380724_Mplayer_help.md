---
title: "Mplayer help"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by hrolfp on 2007-03-10
Hi,

I just installed mplayer, and have binary codecs installed in the appropriate folder. I can play mpg files fine, but when I tried to play .avi files from my dvd I get the error:

Error opening/initializing the selected video_out(-vo) device.

What can I do to fix this?

---

### Post by taurus on 2007-03-10
Go into Preferences and pick "xv" as a driver for video.

---

### Post by hrolfp on 2007-03-10
> **taurus said:**
> Go into Preferences and pick "xv" as a driver for video.

that didn't work :(

---

### Post by taurus on 2007-03-10
Try "x11" then.  Remember, you need to shut it down and open it again after you make the change.

---

### Post by hrolfp on 2007-03-10
x11 worked, thanks a lot!

---

### Post by garybrlow on 2007-03-10
If you installed MPlayer via repos divx files should be played with no problems. You should also take note that an AVI (.avi files) is just video format container not format in itself. AVIs can contain WMVs, Xvids, DIVX, etc. Better use a video file checker to see what kind of video is contained in that AVI. You can also try viewing it via Totem-gstreamer or Totem-xine. Gstreamer and Xine libraries already have their codecs built in especially older/obsolete, both standard and non-standard ones increasing your chances of success.


Cheers!!! :)


GaryBrlow :biggrin:

---

### Post by hrolfp on 2007-03-10
thanks for the info

I got a new problem now though: hitting fullscreen doesn't change the size of the video i'm playing, it only adds a black border around it. How do I fix it?

---

### Post by taurus on 2007-03-10
Try the "xv" driver again.  Again, shutdown it down and open it again after you've made the change or do

```
gmplayer movie.avi
```

---

### Post by hrolfp on 2007-03-10
It works with the x11 driver, but I get the opening/initializing the selected video_out(-vo) device error if I use the xv driver (i've made sure to close the program and reopen after changing driver settings)

---

### Post by taurus on 2007-03-10
Okay, leave the driver as "x11".   Then, post the output of this command here?

```
ls -la ~/.mplayer
```

---

### Post by hrolfp on 2007-03-10
the output is:

total 20
drwxr-xr-x  2 hjs hjs 4096 2007-03-09 23:22 .
drwxr-xr-x 30 hjs hjs 4096 2007-03-10 01:30 ..
-rw-r--r--  1 hjs hjs   44 2007-03-09 23:17 config
-rw-r--r--  1 hjs hjs 2640 2007-03-10 01:30 gui.conf
-rw-r--r--  1 hjs hjs   39 2007-03-10 01:30 gui.history
-rw-r--r--  1 hjs hjs    0 2007-03-10 01:30 gui.pl
-rw-r--r--  1 hjs hjs    0 2007-03-10 01:30 gui.url

---

### Post by taurus on 2007-03-10
Add this line to ~/.mplayer/config.

```
zoom = yes
```
Now, see if you can play a movie with mplayer in fullscreen.

---

### Post by hrolfp on 2007-03-10
that worked. thanks a bunch!

---

