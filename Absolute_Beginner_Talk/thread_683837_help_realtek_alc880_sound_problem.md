---
title: "help realtek alc880 sound problem"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by exneo002 on 2008-01-31
I have an hp pavilion a819n and I put linux mint4.0 basically ubuntu on my box alsa recognizes my alc880 realtek hda-intel card but sound doesn't play I am a newbie sort-of I don't want to wind up compiling drivers through the terminal I always get errors so does any body know about this error and plz help me also I use a mac theme but can't find the apple logo on the menu symbol I don't know how to macmenu hack well plz help so I can kick the windows

---

### Post by eggdeng on 2008-01-31
There are many threads on the forum dealing with this sort of problem. Usually the solution consists in opening an alsa configuration file
```
sudo gedit /etc/modprobe.d/alsa-base
```
and adding a line like
```
options snd-hda-intel model=hp
```
to the bottom of the file. Reboot for changes to take effect. More info at [http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")

---

### Post by exneo002 on 2008-02-01
hey I tried it but I run audio test and I get this error when I run alsa 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

---

