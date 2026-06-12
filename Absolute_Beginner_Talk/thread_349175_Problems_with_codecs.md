---
title: "Problems with codecs"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Hitchhiker42 on 2007-01-29
Okay, I sure this is pretty easy and I'm just overlooking something terribly simple, but I'm having problems getting my media files, such as mp3 and DVDs to play. I installed Media Codecs and AUDDVD using Automatix, but when I try to play an DVD, totem gives me this message "Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it. Please install the necessary plugins and restart Totem to be able to play this media." and when I try to play an mp3, it gives me this message "Totem could not play 'file:///home/rachel/Desktop/13_July_2005_Uptown_Local.mp3'." I'm sure I'm missing something really obvious, and any help would be much appreciated.

---

### Post by taurus on 2007-01-29
Here's a guide.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Fasga on 2007-01-29
I'm not sure what Automatix is, but try:
```
sudo apt-get install w32codecs
```

---

### Post by jvc26 on 2007-01-30
Automatix is an installer which will install all the codecs for you its a GUI interface to make setting up a system easier for someone new to Ubuntu.
Il

---

### Post by mgame2k on 2007-01-30
Um I had the same problem but I downloaded the VLC package which is what I usually used in Windows and works awsome for me.

---

### Post by deadgobby on 2007-01-30
Automatix is a scrip installer that installs a bunch of codecs and other goodies.
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

There is a simular thing called easy ubuntu
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

Gobby

---

### Post by jackrobinson on 2007-01-30
> **Hitchhiker42 said:**
> Okay, I sure this is pretty easy and I'm just overlooking something terribly simple, but I'm having problems getting my media files, such as mp3 and DVDs to play. I installed Media Codecs and AUDDVD using Automatix, but when I try to play an DVD, totem gives me this message "Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it. Please install the necessary plugins and restart Totem to be able to play this media." and when I try to play an mp3, it gives me this message "Totem could not play 'file:///home/rachel/Desktop/13_July_2005_Uptown_Local.mp3'." I'm sure I'm missing something really obvious, and any help would be much appreciated.

install "multimedia players" option from automatix and it will work fine

---

