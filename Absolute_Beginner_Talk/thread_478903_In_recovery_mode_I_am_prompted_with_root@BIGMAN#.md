---
title: "In recovery mode I am prompted with root@BIGMAN:/#"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-19
I entered  (  sudo dpkg -reconfigure xserver-xorg  )  Nothing happens  It tells me options marked [*] produce alot of output - pipe it through less or more

---

### Post by NeoLithium on 2007-06-19
It should be:
```
sudo dpkg-reconfigure xserver-xorg
``` No space between dpkg and -reconfigure :)

---

### Post by swoll1980 on 2007-06-19
cool that worked thanks

I have an Intel 3dagp intagrated video card  The driver it is supposed to use is the   Intel 845gv chipset intagrated controller  what should I enter into the xserver-xorg as my driver

---

### Post by NeoLithium on 2007-06-19
Hmmm, with that intel, you might have to 
```
sudo aptitude install xserver-xorg-video-intel
```

It should give you an Intel Option when you reconfigure.

---

### Post by swoll1980 on 2007-06-19
should i go ahead and try that?

---

### Post by NeoLithium on 2007-06-19
I'd say that's the best bet for that Intel Card

---

### Post by swoll1980 on 2007-06-19
it says identifier  Intel 915 what should I do?

---

