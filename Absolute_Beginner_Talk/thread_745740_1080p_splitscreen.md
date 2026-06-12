---
title: "1080p splitscreen"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by kjhud on 2008-04-04
My resolution is set to 1280x1024 and it causes my screen to be split in half and then flipped. I can't change the resolution or I don't know how to. I have a 1080p 42" Vizio connected with a HDMI cable

---

### Post by kjhud on 2008-04-04
[IMG]http://i26.tinypic.com/awtk0j.jpg[/IMG]

---

### Post by reeseslover531 on 2008-04-04
Can you post your xorg config?  This might shed some light on your problem.

---

### Post by Bölvaður on 2008-04-04
I hope some one isn't as lazy as me tonight.

one word

x server

---

### Post by Bölvaður on 2008-04-04
/var/lib/x11/xorg.conf.

---

### Post by kjhud on 2008-04-04
I can in one minute, what cmd do i type in?

---

### Post by kjhud on 2008-04-05
I have two different xorg.config. I have xorg.conf.md5sum and xorg.conf.roster

---

### Post by kbless7 on 2008-04-05
I believe they mean your /etc/X11/xorg.conf file.

```
sudo gedit /etc/X11/xorg.conf
```

---

