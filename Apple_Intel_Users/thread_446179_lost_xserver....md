---
title: "lost xserver..."
date: 2007-05-16
forum: Apple Intel Users
---

### Post by kysiragi on 2007-05-16
im kinda new to ubuntu, i tried it a few months ago and gave up, anyway i dont know exactly what i did...but xserver wont load and all i can get is a prompt to log in. i cant find the site which i got my information but is there a command or two to reset xserver? i was running i810 1280 x 800. thank you in advance

---

### Post by benanzo on 2007-05-16
do this  at terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

to reset your X server.  This will go through some questions.  Then it will be back to normal.

---

### Post by kysiragi on 2007-05-16
i tried that, after the questions it fails again

---

### Post by benanzo on 2007-05-16
when you're at the terminal type:
```
startx
```

It will give you some error then go back to the prompt.  paste that error here.

---

### Post by ronocdh on 2007-05-16
> **kysiragi said:**
> i tried that, after the questions it fails again
Benanzo's right in that the error output will help everyone, but basically it's probably failing because the wrong options were chosen. Most often it's the driver that's set incorrectly, so feel free to experiment with which driver is being used. Also, you can use the following command to skip all the keyboard questions:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

