---
title: "Screen Resolution"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Reggaeton King on 2006-03-21
On XP, I had my resolution to 1280 x 1024. I would like to know if I can make it bigger on Ubuntu, I went to "Screen Resolution" in the system menu but the largest was 1024 x 768.

---

### Post by patrick295767 on 2006-03-21
[QUOTE=Reggaeton King]On XP, I had my resolution to 1280 x 1024. I would like to know if I can make it bigger on Ubuntu, I went to "Screen Resolution" in the system menu but the largest was 1024 x 768.[/QUOTE]
  
did you try: 
```
dpkg-reconfigure xserver-xorg 
```??

Greetz

---

### Post by Reggaeton King on 2006-03-21
yeah, I made it so the resolution was bigger but it never refreshed or anything, it's still the same resolution

---

### Post by Brunellus on 2006-03-21
you'd still have to restart the x server with a three fingered salute:  CTRL ALT BACKSPACE.

---

### Post by Reggaeton King on 2006-03-21
I figured that before hand and it still didnt work. I should have posted I did restart the system.

---

### Post by timas on 2006-03-22
I'm having a somewhat of the same issue.. in the system settings > display it looks like my monitors keeps being forgoten.. I make it detect my monitor, it finds it.. I change settings and its back at <unknown> as monitor, but now with a 640x480 resolution..

I tried the reconfigure, it worked but only after I had a 640x480 resolution going and only back to 1024..

---

### Post by Brunellus on 2006-03-22
1) what is your hardware? 

2) post the contents of /etc/X11/xorg.conf

---

