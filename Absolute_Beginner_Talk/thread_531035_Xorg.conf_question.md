---
title: "Xorg.conf question"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by nintendoduffin on 2007-08-21
I have a dual-header setup on my main Feisty box with an Nvidia graphics card but when I run the nvidia-settings it sets my keyboard to US so I tried creating a custom xorg.conf file that would allow me to use both monitors while keeping the UK layout on my keyboard. The only thing is when I try to start the graphical X server I get a message saying no screens defined. Does anyone know where I've gone wrong?

[http://cut.and.paste.org/index.php?id=1364]("http://cut.and.paste.org/index.php?id=1364")

---

### Post by kellemes on 2007-08-21
> **nintendoduffin said:**
> I have a dual-header setup on my main Feisty box with an Nvidia graphics card but when I run the nvidia-settings it sets my keyboard to US so I tried creating a custom xorg.conf file that would allow me to use both monitors while keeping the UK layout on my keyboard. The only thing is when I try to start the graphical X server I get a message saying no screens defined. Does anyone know where I've gone wrong?

[http://cut.and.paste.org/index.php?id=1364]("http://cut.and.paste.org/index.php?id=1364")

Watch your /var/log/Xorg.0.log for errors

---

