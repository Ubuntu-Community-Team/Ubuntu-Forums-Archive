---
title: "Sound noise problem"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Yamazaki on 2007-11-08
There is just a noise when i try to play any music file in w/e Media player (Amarok-Totem .. etc), i've read similar topics about this issue here, but seems like they're all unsolved :confused:, somebody help please, i tried adjusting volume control but still, that actually happened after installing a few applications, however the first time running Amarok had this problem, when Totem was working fine, now after installing few apps, i got noise in all media players.

---

### Post by Yamazaki on 2007-11-08
up

---

### Post by Yamazaki on 2007-11-09
up up

---

### Post by ushills on 2007-11-09
Check the PCM volume, I lost all sound a few days ago and for some reason the PCM slider in volume settings was set to zero although I never move this slider.

---

### Post by Yamazaki on 2007-11-09
I just uninstalled Totem Xine and totem works fine with 0 noise, however the problem still exist in Amarok O_o, whats happening?

---

### Post by Yamazaki on 2007-11-09
up

---

### Post by dentaku65 on 2007-11-10
Try to lowering pcm volume:

```
sudo apt-get install alsamixer
```

then type in the terminal window:
```
alsamixer
```

Move with the cursors to PCM and low to 68 or 71and high Master as much as you want, ESC to save

Play an mp3, then reopen alsamixer from a terminal window and during the playing play with Master and PCM volumes, then press ESC to save

---

### Post by Yamazaki on 2007-11-10
It works fine now with some mp3 files, but still certain mp3 files got this noise just in Amarok.

---

### Post by matthewcraig on 2007-11-10
I'll bet Amarok is using a different audio channel.  See if you can configure it.  If not use the GNOME applications that work with the GNOME settings.  Rhythmbox works for me.

---

