---
title: "can't change screen resolution"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by jmtjet on 2006-09-26
When I try to change the screen resolution it reverts back to 800X600 85hz. Would anyone know why this is happening and how to correct it? Thanks.

---

### Post by bodhi.zazen on 2006-09-26
Start with:

Open a terminal and type:
```
sudo dpkg -reconfigure -phigh xserver-xorg
```

Restart with Ctrl-Alt-Backspace

If that does not fix your problem, video card, monitor??

---

### Post by BlackNash on 2006-09-26
Or simply you can make it manually
#sudo nano /etc/X11/xorg.conf
Ctrl + W: to look for Screen 
and depending of the Color Mode that you are using (16 o 24):
add Mode "1024x768"(this is the new) "800x600" "640x480".

Of all manners ,check your viedo card, monitor,like bodhi.zazen said 
thus:
#sudo dpkg -reconfigure xserver-xorg
and fix it on case of mistakes

---

### Post by jmtjet on 2006-09-26
Thanks guys, ran the command and the resolution problem is now solved. :)

---

