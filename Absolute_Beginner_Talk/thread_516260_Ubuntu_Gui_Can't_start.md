---
title: "Ubuntu Gui Can't start"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Solidad on 2007-08-03
i can't seems to go to, ubuntu windows like interface. it seems i set the wrong driver when i was trying to get it to go 1280x1024. 

how can get back the generic driver settings for my video?

---

### Post by Rotaj on 2007-08-03
You might want to try this: 

[COLOR="Indigo"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

---

### Post by Solidad on 2007-08-03
i'll type that on the recovery console?

---

### Post by coolen on 2007-08-03
Yes. Although calling it a recovery console isn't really accurate: it's a very powerful, fully featured interface to your system. Just not as nice as some.

---

### Post by Solidad on 2007-08-03
ok, i'll try.

---

### Post by Solidad on 2007-08-03
its not working. is there a way to use the install cd to configure it back to what it was?

---

### Post by coolen on 2007-08-03
What graphics card do you use?

---

### Post by Solidad on 2007-08-03
a nvidia GeForce FX5200

---

### Post by gimpy04 on 2007-08-03
[B]i belive to get your nvidia drivers its apt-get nvidia-glx
it may be sudo apt-get nvidia-glx hope that works fro you[/B]

---

### Post by Solidad on 2007-08-03
can i do that? without the Gui?

---

