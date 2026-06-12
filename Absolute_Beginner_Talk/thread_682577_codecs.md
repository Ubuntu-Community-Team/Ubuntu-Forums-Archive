---
title: "codecs"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by jesterjoker on 2008-01-30
Hi 
Cannot get my MP3's or dvd's to play. Not so sure installing Ubuntu was a good idea, Just fed up.

Please HELP

---

### Post by jan quark on 2008-01-30
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

this guide will help you to enable the ability to play restricted formats

mp3 and dvd work flawlessly in ubuntu dont loose the hope :)
if there are questions ask them we will help

---

### Post by jesterjoker on 2008-01-30
tried installing from Add/Remove, this is what i get

The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection

beyond that, nothing happens

---

### Post by hyper_ch on 2008-01-30
post the output of

```

cat /etc/apt/sources.list

```

---

### Post by jan quark on 2008-01-30
is seems your source list is not enabled

go to the source window in the menu and check all available sources for instance multiverse

then open the terminal and type

```
sudo apt-get update
```

this will refresh your source list

try to download the codes again

---

### Post by tizza10 on 2008-01-30
Give Automatix a try if your still having problems. [http://www.getautomatix.com](http://www.getautomatix.com).

---

### Post by hyper_ch on 2008-01-30
Automatix is not recommended for installation.

---

### Post by jesterjoker on 2008-01-30
seem to be downloading package files now, approx 20mins to , i'll see then. thanks for the help.

---

