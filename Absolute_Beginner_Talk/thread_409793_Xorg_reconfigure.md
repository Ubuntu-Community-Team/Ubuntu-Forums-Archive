---
title: "Xorg reconfigure"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-04-15
Since I just reinstalled Ubuntu, I forgot how to reconfirgure Xorg via the terminal, and I'm not talking about opening the text file.

 What was that command to completely reconfigure the Xorg server? I'm getting kind of tired with the resolution set at 640*480 @ 50 hertz...

---

### Post by Maestro23 on 2007-04-15
Here you go:

> sudo dpkg-reconfigure xserver-xorg

---

### Post by ZeroWing on 2007-04-15
I love you.

 Only thing I've never figured out, though, was what the Horzsync and vertsync were, or how to configure them. I don't remember, but I believe that they had to do with the refresh rate. How could I set these to around 50-85 hertz?(Old monitor. All it can handle.)

---

### Post by rajeev1204 on 2007-04-15
select the simple option when it passes the monitor the autodetect phase

the other options are medium and advanced .


in simple it just says 17 inch generic and works fine for me

---

### Post by nudnik on 2007-04-15
> **ZeroWing said:**
> I love you.

 Only thing I've never figured out, though, was what the Horzsync and vertsync were, or how to configure them. I don't remember, but I believe that they had to do with the refresh rate. How could I set these to around 50-85 hertz?(Old monitor. All it can handle.)

For a quick generic reconfigure for those less experienced:

sudo dpkg-reconfigure -phigh xserver-xorg

This automatically sets everything save the resolution. May not provide the best performance, but handy to restore GUI quickly.

---

### Post by ZeroWing on 2007-04-15
Alright. The screen resolution window says I'm running at 51Hertz, but looks like ~70 to me. I'd like 85, but this is okay.


 Can't trust Ubuntu.... it's shifty... like poodles....

---

