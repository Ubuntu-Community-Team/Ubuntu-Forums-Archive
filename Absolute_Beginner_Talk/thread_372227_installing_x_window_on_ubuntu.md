---
title: "installing x window on ubuntu"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by hardipdhillon on 2007-02-27
I am a newbie to linux i have installed ubuntu server 6.0 ,but it is just command based ,how can i install graphical windows on it and from where can i download the pacakge.

---

### Post by timjayko on 2007-02-27
why install just server version and not regular version?

---

### Post by Quillz on 2007-02-27
> **hardipdhillon said:**
> I am a newbie to linux i have installed ubuntu server 6.0 ,but it is just command based ,how can i install graphical windows on it and from where can i download the pacakge.
Try "sudo apt-get kdebase." That should install the latest version of KDE.

---

### Post by hardipdhillon on 2007-02-28
i run the command  "sudo apt-het kdebase" but it tells invalid operation kdebase .i think i need to download the package can u please tell me where can i find it.

---

### Post by 3rdalbum on 2007-02-28
> **hardipdhillon said:**
> i run the command  "sudo apt-het kdebase" but it tells invalid operation kdebase .i think i need to download the package can u please tell me where can i find it.

The wrong command was given above; this one should do the trick:

```
sudo apt-get install kdebase kdm xserver-xorg
```

---

