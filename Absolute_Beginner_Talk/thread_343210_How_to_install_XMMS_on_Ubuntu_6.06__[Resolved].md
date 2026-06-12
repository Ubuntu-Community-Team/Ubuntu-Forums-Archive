---
title: "How to install XMMS on Ubuntu 6.06 ??? [Resolved]"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by bimaljr on 2007-01-21
Hi,

I love so many MP3 files... I want to install XMMS to play my MP3 files.
I have searched for this but not find any good link...
Help me on installing XMMS on my Ubuntu 6.06 system...

Thanks in advance...

---

### Post by xyz on 2007-01-21
Application > Accessories > Terminal and type:
```
sudo aptitude install xmms
```
If you run into problems when loading it, post the output of:
```
lspci
```
to see what card you have.

---

### Post by bimaljr on 2007-01-21
Hey thanx... I have now XMMS on my system... (currently listening songs)

Thanx once again.. :D

---

### Post by Sef on 2007-01-21
Best to do:

```
sudo aptitude update
```

then

```
sudo aptitude install xmms
```

---

