---
title: "how do I install KDE? or get Ubuntu with KDE?"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by reynoldlariza on 2005-07-06
i've been a bit comfortable with ubuntu linux now for the past few weeks of playing with it. However, I missed my beloved KDE. How do I install it? or get what called "Kubuntu"? 
Sorry, but I'm a noob strugggling to be not noob :P

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=reynoldlariza]i've been a bit comfortable with ubuntu linux now for the past few weeks of playing with it. However, I missed my beloved KDE. How do I install it? or get what called "Kubuntu"? 
Sorry, but I'm a noob strugggling to be not noob :P[/QUOTE]

You got broadband? Then do this:

> sudo apt-get install kubuntu-desktop

thats it.

---

### Post by SGC on 2005-07-06
Open **/etc/apt/sources.list** and add the following:
```

deb http://kubuntu.org/hoary-kde341 hoary-updates main

```

Then do:
sudo apt-get update
sudo apt-get install kubuntu-desktop

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=SGC]Open **/etc/apt/sources.list** and add the following:
```

deb http://kubuntu.org/hoary-kde341 hoary-updates main

```

Then do:
sudo apt-get update
sudo apt-get install kubuntu-desktop[/QUOTE]

Good call. Also make this line look like this before you close and save the text file:

> 
## deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


---

