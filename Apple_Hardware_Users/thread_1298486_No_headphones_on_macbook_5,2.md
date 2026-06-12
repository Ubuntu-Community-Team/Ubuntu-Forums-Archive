---
title: "No headphones on macbook 5,2"
date: 2009-10-22
forum: Apple Hardware Users
---

### Post by nexx892 on 2009-10-22
The optical out works good and so does the speakers but the normal speakers do not work. Any fixs?

---

### Post by amd-64 on 2009-10-23
try gnome-alsamixer and check if any channels are muted.

---

### Post by DPic on 2009-10-24
this still seems to be a problem in karmic. any solutions found?

---

### Post by nexx892 on 2009-10-24
nope

---

### Post by BuffaloBill on 2009-11-16
Downloading gnome-alsamixer and unmuting the "speaker" did the trick for me!

---

### Post by linuxopjemac on 2009-11-16
you can also do it in a terminal:

```
alsa-mixer
```

unmute the last speaker on the right

---

### Post by aprigiosimoes on 2009-11-16
#dpkg-reconfigure linux-sound-base

SELECT >>> ALSA

#alsactl restore

#alsamixer
and abillitie the mic and headphone.



tanks

---

### Post by zAfi on 2009-11-16
lol, and i only get sound through the headphones! :P (MB 5,1, late '08 )

---

### Post by alexmurray on 2010-01-14
I've just posted a patch to enable muchly improved sound experience with MB 5,1 - ie. master controlled headphones volume and auto-muting of speakers when headphones are plugged in on MacBook (Pro) 5,1 / 5,2: [http://ubuntuforums.org/showthread.php?t=1379971](http://ubuntuforums.org/showthread.php?t=1379971) - see here to try it out.

---

