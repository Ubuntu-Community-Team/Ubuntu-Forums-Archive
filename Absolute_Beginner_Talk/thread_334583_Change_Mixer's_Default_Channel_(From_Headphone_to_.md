---
title: "Change Mixer's Default Channel (From Headphone to PCM)"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by gidra on 2007-01-09
- Just got my HDA-Intel headphone output to work on Asus A3Ac notebook after following this tutorial -> [http://www.dev-board.com/](http://www.dev-board.com/)

- Now I want to change the mixer's default channel from headphone to pcm so that when i control the volume from keyboard shortcut (eg. Fn+F12 to increase volume) it would affect the pcm channel not the headphone's. Any ideas please ?

---

### Post by xyz on 2007-01-09
Hi,
In a terminal, copy/paste:
```
alsamixer
```
and see what you've got on in there - use left/righ arrows.

---

### Post by gidra on 2007-01-09
Alsa mixer just shows the channels i.e. from left to right -> Headphone, PCM, Front, CD etc.
Now how do i make PCM default?

---

### Post by xyz on 2007-01-09
Try also Applications > Sound & Video > Volume Control > Playback and then you should be able to check PCM

---

### Post by gidra on 2007-01-09
There is no option to check a channel for default. Options are either to mute/unmute or split left and right channels :-?

---

### Post by xyz on 2007-01-09
Let's try [T H I S]("http://ubuntuforums.org/showthread.php?t=199579&page=2&highlight=PCM+default")

---

### Post by gidra on 2007-01-09
Thanks for the reply. Tried to mess up something with keytouch but it isn't working correcty and since i'm a total noob I don't know what is going on. There isn't a simpler method?

---

### Post by gidra on 2007-01-09
No ideas ?:(

---

