---
title: "Where can I get nvidia drivers for a 2.6.19 custom kernel"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by uriahs on 2006-12-16
Hi, does anyone know where I could get nvidia drivers for a 2.6.19 custom kernel?

Anyone know if I have to compile it my self if it's a custom kernel?

Should I use a pre-packaged 2.6.19 kernel?

Or is 2.6.19 too new, should I down grade to 2.6.18 for now?

I don't like the 2.6.17 kernel, it seems to have a problem with my Audio and ALSA.

Any help is much appreciated.

---

### Post by Ecthelion on 2006-12-16
Hey,

I followed [this guide]("http://ubuntuforums.org/showthread.php?t=263851&highlight=AIGLX+beryl") to install Nvidia. I choosed the second option and downloaded the Nvidia drivers with the Nvidia script.
I recal that my kernel was not recognized and that it compiled it automatically.
So this should work with a selfcompiled kernel too I think.

I hope this helps

---

### Post by uriahs on 2006-12-16
> **Ecthelion said:**
> Hey,

I followed [this guide]("http://ubuntuforums.org/showthread.php?t=263851&highlight=AIGLX+beryl") to install Nvidia. I choosed the second option and downloaded the Nvidia drivers with the Nvidia script.
I recal that my kernel was not recognized and that it compiled it automatically.
So this should work with a selfcompiled kernel too I think.

I hope this helps

Yeah, I tried that however when it came up it said it could not find screens or something. I have that configured on here at the moment (just don't have it setup in /etc/X11/xorg.conf).

However I didn't do the clean up stuff, I'll give that a try in a second.

---

### Post by uriahs on 2006-12-16
Well it worked. Unfortunately it just booted a blank screen, in the Xorg.0.log file it says a few things...
```

(WW) NVIDIA(0): No valid modes for "1920x1440"; removing.
(WW) NVIDIA(0): No valid modes for "1856x1392"; removing.
(WW) NVIDIA(0): No valid modes for "1792x1344"; removing.
(WW) NVIDIA(0): No valid modes for "1280x854"; removing.
(WW) NVIDIA(0): No valid modes for "1200x800"; removing.
(WW) NVIDIA(0): No valid modes for "1152x768"; removing.

```

and...

```

(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000000, 0x00000624)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x00000000, 0x00000624)
(II) NVIDIA(0): Setting mode "1920x1200"
(WW) NVIDIA(0): WAIT (2, 1, 0x8000, 0x00000000, 0x000006e8)
(WW) NVIDIA(0): WAIT (1, 1, 0x8000, 0x00000000, 0x000006e8)
(WW) NVIDIA(0): WAIT (2, 3, 0x8000, 0x00000000, 0x00000d60)
(WW) NVIDIA(0): WAIT (1, 3, 0x8000, 0x00000000, 0x00000d60)
(WW) NVIDIA(0): WAIT (2, 11, 0x8000, 0x00000000, 0x00000d80)

```

For some reason it didn't support 1920x1440, which I believe is my default.

I have attached the entire log so you can see.

Any insight would be much appreciated.

---

### Post by OffHand on 2006-12-16
Logout, press ctrl+alt+F1 and login using text mode.

Then type:
```
sudo dpkg-reconfigure xserver-xorg
```Answer all the questions. If you do not know the answer pick default.

Then type:
```
sudo /etc/init.d/gdm restart
```

This will reconfigure X for you.

---

### Post by uriahs on 2006-12-17
Hrmmm, even after running the above it was still black. I'm not quite sure what's wrong.

---

### Post by Ecthelion on 2006-12-17
> Hrmmm, even after running the above it was still black. I'm not quite sure what's wrong.

That's strange. Isn't there any error that comes up on the terminal screen?
(The screen you used to do sudo /etc/init.d/gdm start)
(btw do you use gnome or kde?)

Or can you find an error in any system log?

---

### Post by uriahs on 2006-12-21
I use gnome. There were no messages what so ever, plain black. I'm going to try again, from the top tomorrow... it started to make me angry before, so I thought I'd give it a rest.

---

