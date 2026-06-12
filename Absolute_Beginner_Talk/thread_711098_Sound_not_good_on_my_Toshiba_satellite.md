---
title: "Sound not good on my Toshiba satellite"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by chemicalgr on 2008-02-29
I have connected  my *sound system  with my toshiba satellite but the sound output is still form the internal speakers of the laptop not from the sound system
what should i do?

*home stereo
thanks

---

### Post by Cappy on 2008-02-29
```
sudo su
```
and then
```
echo "options snd-hda-intel position_fix=1 model=lenovo" >> /etc/modprobe.d/alsa-base
```

(Assuming you are using gutsy)

---

### Post by chemicalgr on 2008-02-29
but i don't have lenovo

---

### Post by chemicalgr on 2008-02-29
You mean that the lenovo doesn't make a difference cause they are all the same?

---

### Post by Cappy on 2008-02-29
> **chemicalgr said:**
> You mean that the lenovo doesn't make a difference cause they are all the same?

Correct.

---

