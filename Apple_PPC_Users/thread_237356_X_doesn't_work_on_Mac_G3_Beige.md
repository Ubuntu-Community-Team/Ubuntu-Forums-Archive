---
title: "X doesn't work on Mac G3 Beige"
date: 2006-08-16
forum: Apple PPC Users
---

### Post by Marco Renoldi on 2006-08-16
Hello!
I just installed ubuntu dapper on my G3 Beige. The installation process was OK but after the reboot X doesn't start. It says:
"Screen(s) found but none have a usable configuration"
Googling around I found some hints on passing arguments to the kernel but none worked for me. Does anybody have ubuntu up and running on a G3 Beige? which kernel argument is the one that works?
Many thanks
Marco

---

### Post by 3rdalbum on 2006-08-16
I'm assuming first off that your Mac has enough memory to run Ubuntu with a GUI.

I don't think it's a kernel argument that you've got to pass, I think you just need to reconfigure Xorg (probably none of its developers have Oldworld Macs).

When you get the terminal after the error message appears, type:

```
sudo dpkg-reconfigure xserver-xorg
```

If asked for a password, just press Return.

I'm not sure what settings to go for from there, but you must manually configure the video card and possibly the monitor too. Try telling it to use the "vesa" driver for the video card, and doing a "Simple" configuration of the monitor. If that doesn't work... then trial-and-error is your only option unless someone else knows what settings to use?

(I never had an Oldworld with enough memory to start X)

---

### Post by Marco Renoldi on 2006-08-19
I do have 512MB...
I tried and re-tried many configuration ... no luck!
Anyone got some hints?
marco

---

### Post by AndrewBarber on 2006-08-20
Hey, you may have problems with your xorg.conf.
I have just replied to somebody else having problems, so you can try it out too.
It is found [here](http://ubuntuforums.org/showthread.php?p=1400643#post1400643).
Good luck, **make sure you back up your xorg.conf**

---

