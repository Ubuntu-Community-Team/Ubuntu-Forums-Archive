---
title: "Volume controle dead?"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-21
After restarting my computer, my volume controle is not working anymore? It has a small red X over it, and when I try to open it, it says:

> Error
Registry is not present or it is corrupted, please update it by running gst-register

Or if I try to go to Preferences nothing happends.

I can still play musik, and all sounds are working fine.

Any idea what this could be? I use that thing pretty much.

---

### Post by Mustard on 2006-04-21
Try this in terminal..

```
gst-register-0.8
```

---

### Post by aktiwers on 2006-04-21
[quote=Mustard]Try this in terminal..

```
gst-register-0.8
```[/quote]

Thanks a lot! That worked!

What was the problem? And what did that code do? :confused:

---

### Post by Mustard on 2006-04-21
I got it from this guide.  Apparently it registers all the gstreamer stuff for multimedia. *shrugs* :)

[http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies)

I've had the same problem myself a long time ago (while mucking around with Dapper Drake), so I just knew what worked for me.  The technicalities of it are a bit beyond my knowledge. :D

The problem was basically what the error messages said.  The register was not present or was corrupted.  I'd speculate that it was option B.

---

