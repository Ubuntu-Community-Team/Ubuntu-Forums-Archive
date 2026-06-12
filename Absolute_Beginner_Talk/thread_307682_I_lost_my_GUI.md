---
title: "I lost my GUI"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by 4-8-4 Northern on 2006-11-26
I installed Edgy Eft. Rebooted. No problem. Remove Gnome and added KDE. Rebooted. No problem. Added some programs, Rebooted. No problem. Added a hole bunch more programs. Rebooted. Now logon is text based and I get a command line instead of the KDE desktop. Can I fix this?

---

### Post by buddie on 2006-11-26
login and run
```
startx
```
and see what it says...

---

### Post by 4-8-4 Northern on 2006-11-26
OOPS! One of the things I added was an nvidia driver. I type startx and got **Fatal server error no screens found. XIO: fater IO error104 (connection reset by peer) on x server ":0.0"**

---

### Post by 4-8-4 Northern on 2006-11-27
I fixed the problem. I found a post dealing with startx and video drivers and ran xorg to reconfigure the video driver. [http://www.ubuntuforums.org/showthread.php?t=304229&highlight=video+driver](http://www.ubuntuforums.org/showthread.php?t=304229&highlight=video+driver)

---

### Post by Paul133 on 2006-11-27
Yeah. Graphics drivers will usually kill X more than anything else. I don't have a graphics card, so I wouldn't know.

---

### Post by adam.tropics on 2006-11-27
> **Paul133 said:**
> ... I don't have a graphics card, so I wouldn't know.


Sorry?

edit: lol you must be running UbuntuAE (Abacus edition)!!

---

