---
title: "Loading Bar doesn't appear..."
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Yaywalter on 2008-04-17
So recently, I installed Ubuntu on my laptop. And for some reason, during startup, no loading bar ever shows up. My screen remains black until the login screen. 

And it feels like it takes forever to start up, too. I'm not sure whether it is actually taking longer to start up than it's supposed to, or if it just feels like it because the screen is black, but it takes longer than XP did... feels almost twice as long.

Anyone know what's wrong?

---

### Post by TeoBigusGeekus on 2008-04-17
Type in a terminal
```
sudo gedit /boot/grub/menu.lst
```
and post us the contents of the file. It might be the splash option in the grub menu...

---

### Post by divague on 2008-04-17
check this thread
[http://ubuntuforums.org/showthread.php?t=754388](http://ubuntuforums.org/showthread.php?t=754388)

---

### Post by Yaywalter on 2008-04-17
> **TeoBigusGeekus said:**
> Type in a terminal
```
sudo gedit /boot/grub/menu.lst
```
and post us the contents of the file. It might be the splash option in the grub menu...
Alright, will do once I get home.

---

### Post by SunnyRabbiera on 2008-04-17
I am all too familiar with this issue, I had it myself.
your better bet to fix this is to wait another 7 days till hardy comes out and see how that works.

---

### Post by Yaywalter on 2008-04-18
> **SunnyRabbiera said:**
> I am all too familiar with this issue, I had it myself.
your better bet to fix this is to wait another 7 days till hardy comes out and see how that works.
I'll take your word for it. Hopefully hardy works better for me... this isn't the only issue I've had. :lolflag:

---

### Post by joshrobinson on 2008-04-18
```
sudo gedit /etc/usplash.conf
```

enter your resolution

then run this

```
sudo update-usplash-theme usplash-theme-ubuntu
```

---

