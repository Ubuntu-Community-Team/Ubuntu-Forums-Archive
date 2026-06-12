---
title: "Who hasn't hear this one before..."
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by eyesrglazed on 2007-02-06
I'm busy trying to install Ubuntu on my computer right now. I've got it completely wiped, and everything is running smoothly. My last obstacle: getting the commands to install the Gnome GUI. All I'm looking for is the "sudo apt-get install" commands, and I had them before, but apparently, I have a poor memory buffer in my head. (Poor computer joke. Sorry. =P)

Does anyone know the exact packages I need to install in order to have the Gnome desktop environment?

---

### Post by 23meg on 2007-02-06
If you use the desktop CD to install Ubuntu and do a regular install, you won't need to install GNOME with commands separately.

---

### Post by eyesrglazed on 2007-02-06
The CD that I have only installs the text interface. I had a friend install this for me before, but it crashed, so I have to reistall it.

---

### Post by jvc26 on 2007-02-06
Which version of Ubuntu are you trying to install? As if it is the text based one again you don't need to use CLI to install the GUI - Is it a really old version?
Il

---

### Post by 23meg on 2007-02-06
You probably did a server install. If you have no means of downloading the desktop CD, you can install with ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by R3linquish3r on 2007-02-06
could be a server disk. either way the command you want is sudo apt-get install ubuntu-desktop

---

### Post by eyesrglazed on 2007-02-06
It is a server disk... S'pose I should've mentioned that before. I'll try those commands and get back to you guys.

---

### Post by 23meg on 2007-02-06
> **R3linquish3r said:**
>  sudo apt-get install ubuntu-desktop
*aptitude* is a better choice when installing metapackages with lots of dependencies.

---

### Post by h2gofast on 2007-02-06
I hope you have broadband.

---

