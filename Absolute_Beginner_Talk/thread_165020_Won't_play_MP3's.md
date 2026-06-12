---
title: "Won't play MP3's"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by quincyjones on 2006-04-23
Hi, 
Ubuntu won't recognise / play MP3's.
I have w32codesc installed, as well as gstreamer0.8-mad.
What should I do?

Thanks in advance! ;)

**edit/:**
I realised I don't have an mp3 problem, it's a CD/DVD player problem, it won't recognise any data files. From my mem stick, mp3's work fine.
I'll put up a new post, 
Thanks anyway

---

### Post by Qrk on 2006-04-23
Looking at the wiki, it recommends installing the akode-mpeg package if you are running KDE.

```
sudo apt-get install akode-mpeg
```

Its worth a shot.

---

### Post by Nequeo on 2006-04-23
[QUOTE=quincyjones]Hi, 
Ubuntu won't recognise / play MP3's.
I have w32codesc installed, as well as gstreamer0.8-mad.
What should I do?

Thanks in advance! ;)[/QUOTE]

What version of Ubuntu are you running? 5.10 or 6.06 beta?

(If you don't know off the top of your head, just hit Ctrl+Alt+F1 - take a look at the version number, then hit ctrl+alt+F7 to get back to your desktop)
.

---

### Post by ComplexNumber on 2006-04-23
[quote=quincyjones]Hi, 
Ubuntu won't recognise / play MP3's.
I have w32codesc installed, as well as gstreamer0.8-mad.
What should I do?

Thanks in advance! ;)[/quote] try typing the following on the command line: "gst-register"(without the quotes). then try again.

---

