---
title: "firefox plugin missing"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by 4seasonphotos on 2007-07-04
Hello I am using Fiesty Fawn Ubuntu and I also use firefox but it says I am missing a plug in for video.. It appears their is no plugin.. Does anyone know what I can use and how to install it? Thanks!  :D

---

### Post by Malibu Illusion on 2007-07-04
Without knowing exactly what type of media you're attempting to play, try:

```
sudo aptitude install totem-mozilla
```

---

### Post by lisati on 2007-07-04
Depending on the website and the plugin required, Firefox can sometimes download it for you automatically. Have a look for a "click here to install plugin" message.

---

### Post by bren on 2007-07-04
try this

> 
sudo apt-get  install flashplugin-nonfree

you will need to enable the right repository (multiverse?) in /etc/apt/sources.list

---

### Post by 4seasonphotos on 2007-07-04
I am sorry but where exactly do I enter this code?? I am not real familiar with Ubuntu.. Sorry.. 



> **bren said:**
> try this



you will need to enable the right repository (multiverse?) in /etc/apt/sources.list

---

