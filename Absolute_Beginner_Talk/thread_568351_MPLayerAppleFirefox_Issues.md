---
title: "MPLayer/Apple/Firefox Issues"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-10-05
Hey there, using automatix, I loaded up the mplayer application and codecs along with the firefox plugin. I'm having no troubles running pretty much all movies, except when I go to Apple's trailer website, I can seem to get any of the quicktime stuff running or going. I'm running 2.0.0.6 of firefox. Any ideas or opinions on how to get everything up and running well? Thanks!

---

### Post by Tumpster on 2007-10-11
Bump Bumpity Bump BUmp Bump

---

### Post by philinux on 2007-10-11
I'm using mplayer from synaptic and it comes with all the plugins I think. In a firefox window type in the address bar

```
about:plugins
```

and have a look at whats installed already.

---

### Post by wayneschutz on 2007-10-11
Here's what I did to make it work:

1. Go to the apple trailer website and select a trailer.
2. Right click on the trailer and select: "Open with Movie Player"
3. Totem will start and tell you that it needs to install additional codes, click OK
4. Select all the codecs that display, you'll get a message about these being "bad" codecs.
5. After that, the Totem player plays the clip and so does the one embedded in the web-page.

**actually** I had to do this procedure TWICE to get all the codecs for some reason .....

btw... by "about: plugins" shows:

QuickTime Plug-in 7.1.3

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes

....

Good luck -w

---

### Post by Tumpster on 2007-11-15
Got it, I unistalled it and reloaded it again, works now!! :)

---

### Post by Ansenyi on 2007-11-23
I also had some issues, but I got it working by uninstalling the mozilla-plugin-vlc.

---

