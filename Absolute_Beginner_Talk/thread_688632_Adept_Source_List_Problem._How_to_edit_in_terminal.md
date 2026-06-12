---
title: "Adept Source List Problem. How to edit in terminal or kate?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by WayOutWest on 2008-02-05
I wrote the source list incorrectly for Adept and now it won't start saying their is an error with the list. Can someone tell me how to update that manually from the terminal (step by step) or with Kate?

---

### Post by emarkd on 2008-02-05
you can edit that by running:

```
kdesu kate /etc/apt/sources.list
```

---

### Post by akiratheoni on 2008-02-05
If you wanted to do it in the terminal, it would be:
```
sudo vi /etc/apt/sources.list
```

But Kate would probably be easier.

---

### Post by Nythain on 2008-02-05
or
```

sudo nano /etc/apt/sources.list

```
and or
```

sudo vi /etc/apt/sources.list

```
both from a terminal/command line, depending on wether you prefer nano or vi... there are other terminal text editors too, so whatever you prefer

---

### Post by WayOutWest on 2008-02-05
Thanks so much. I found it before you said that but I didn't have write access because I didnt know about kdesu. Thanks again. 

love this forum:D

---

### Post by akiratheoni on 2008-02-05
> **WayOutWest said:**
> Thanks so much. I found it before you said that but I didn't have write access because I didnt know about kdesu. Thanks again. 

love this forum:D

Yeah, just remember that if you're launching a graphical application through a terminal, you're going to want to use kdesu... IIRC, Kate won't launch if you're using sudo instead of kdesu.

---

### Post by MasterXandrex on 2008-02-05
Damn KDE users, I had no idea what kdesu was... haha. For reference, the gnome command for this is gksudo.


Xan

---

