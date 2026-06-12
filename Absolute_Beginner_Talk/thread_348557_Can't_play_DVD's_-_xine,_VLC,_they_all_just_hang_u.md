---
title: "Can't play DVD's - xine, VLC, they all just hang up"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Armor on 2007-01-28
Title more or less sums it up. Brand new to Edgy.

This link [https://help.ubuntu.com/ubuntu/desktopguide/C/video.html#dvdplayback](https://help.ubuntu.com/ubuntu/desktopguide/C/video.html#dvdplayback) gives good directions on how to get DVD playback. 
Step 1 I did, libdvdread3 is installed
Step 2 I can't get past. Whenever I type in 

"sudo /usr/share/doc/libdvdread3/examples/install-css.sh"

it says unknown command. I tried replacing the "usr" part with my login to Ubuntu (which is "leigh") so it reads

"sudo /leigh/share/doc/libdvdread3/examples/install-css.sh"

but I get the same result. If I put in a DVD and try to open gxine or VLC, the system just hangs and does nothing. Neither program opens, and the read light on my DVD player just remains lit, as well as the HDD light on my computer. It takes about 5 minutes before the DVD tray opens up.
Any help here would be GREATLY appreciated!

---

### Post by RomeReactor on 2007-01-29
In Edgy the correct location is "/usr/share/doc/libdvdread3", so the correct command is:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Check [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability") guide.

Totem-Xine works great; Gstreamer can't handle DVD's yet.

---

### Post by Armor on 2007-01-29
Well thanks for the proper command line, that worked, so I've been able to get past step 2, but it still isn't working. gxine is still hanging up. Won't do anything...starting to lose hope here. I just end up having to force quit because it just locks up

---

### Post by RomeReactor on 2007-01-29
I don't have Gxine installed, so i can't say what the problem is there; try running it from a terminal:

```
gxine
```

and open a DVD, then look at the terminal output. Totem works fine for me, maybe you should try with it.

---

### Post by Armor on 2007-01-29
I just restarted and that worked. NOW the problem is with playback. If it's in full screen mode, just about ever 3 seconds, right on cue, it flicks off for half a second, then goes back on. Video and audio stop, indeed the whole screen goes off, then it resumes where it left off. It only does this in full screen mode, not when it's playing in a smaller viewing

CORRECTION: The audio remains and plays fine, just every 3 seconds the whole screen flicks off then on again

EDIT: I tried it with VLC and it plays fine at full screen, gxine seems to be the only program that flickers like that...

---

### Post by Denn1s on 2007-01-29
are you using beryl or compiz? video reproduction is somethimes buggy under them

---

### Post by Armor on 2007-01-29
I don't know what those are, and I don't know how to check :( :confused:

---

### Post by RomeReactor on 2007-01-29
Most likely you don't have either; they don't come with Ubuntu. In the off-chance that you don't have [DMA]("http://en.wikipedia.org/wiki/Direct_memory_access") enabled (and this may be why playing DVD's is slow), try this in a terminal:

```
sudo hdparm -d1 -k1 /dev/hdc
```

where "hdc" is my dvd reader (you should put the correct designation of your own there).

---

### Post by Armor on 2007-02-01
Thanks man, seems to work

---

