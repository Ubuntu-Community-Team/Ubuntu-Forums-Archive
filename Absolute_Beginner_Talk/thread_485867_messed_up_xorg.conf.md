---
title: "messed up xorg.conf"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by xxchrisxx555 on 2007-06-27
i messed up my xorg.conf and i have a copy of it but when i boot up i get a message saying x couldnt start and shows me whats wrong but after that i get no terminal

does anyone know how to fix this

---

### Post by speaker219 on 2007-06-27
go in terminal and type:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by xxchrisxx555 on 2007-06-27
i cannot open a terminal
i just get a blank screen

---

### Post by Cypher on 2007-06-27
..and if you have a copy, then 
```

sudo cp /etc/X11/<xorg.backup.filename> /etc/X11/xorg.conf

```

P.S, hit CTRL-ALT-F1 to get the regular text console, login and do either of the above commands..

---

### Post by xxchrisxx555 on 2007-06-27
that did it

---

### Post by speaker219 on 2007-06-27
> **xxchrisxx555 said:**
> that did it

Which one worked? curious to know

---

### Post by tellos on 2007-09-17
Ahahah amazing...

accually I used both solution, the first one to make a new xorg.conf and being able to boot in gui, then I luckily realised that in /etc/X11/ there was a xorg.conf.(dateofbackup).

then I used the other solution to change xorg.conf to the backup...and it worked....thank you soooo much

---

### Post by corevette on 2007-09-17
For the record, the next version of Ubuntu (Gutsy Gibbon) features a bullet proof X-server
So eventually the crashes will disappear
[https://wiki.ubuntu.com/BulletProofX](https://wiki.ubuntu.com/BulletProofX)

---

