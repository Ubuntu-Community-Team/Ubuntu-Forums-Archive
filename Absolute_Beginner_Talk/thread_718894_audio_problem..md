---
title: "audio problem."
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by chips24 on 2008-03-08
im having a problem were most times the audio starts making a rattling sound like a helicopter.
i just got my sound working a while ago but its very low quality and choppy.

---

### Post by sanmeetkanhere on 2008-03-08
Do
```
sudo nano /etc/modutils/alsa
```

and add this to the end of the file

```

# ALSA
alias char-major-116 snd
alias snd-card-0 snd-via82xx

# OSS
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
```

finally update:
```
sudo update-modules
```

and the sound should be ok now. Make sure the volume is not 100% as it may be causing some distortion.

Peace out,
Sanmeet

---

### Post by chips24 on 2008-03-08
this didnt do anything. didnt let me close the file and didnt have a body.

---

