---
title: "play dvd video"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by ranlil on 2008-04-16
g

---

### Post by arijarot on 2008-04-16
what's your question?

---

### Post by Meskarune on 2008-04-16
Install VLC player? I'm guessing you're having problems? Also, use your package manger to install gstreamer codecs. Just search for "gstreamer" And install what you get.

---

### Post by crjackson on 2008-04-16
Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

---

### Post by Promaster91 on 2008-04-16
This should solve it.
[http://ubuntuforums.org/showthread.php?t=709613](http://ubuntuforums.org/showthread.php?t=709613)

---

