---
title: "Gutsy G++"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by PropheticAngel on 2007-11-17
I am trying to install G++ on my gutsy installation, but whenever I try, it tells me to insert the disc and press enter.

I don't have the disc readily available anywhere and I don't want to burn another copy, is there a way to install G++ without the hassle of re-burning the image?

---

### Post by taurus on 2007-11-17
Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Save it and run

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by Frak on 2007-11-17
Goto System->Administration->Software Sources, uncheck "CD-ROM Gutsy", and try again, but doing
```
sudo aptitude install build-essential
```
instead

---

