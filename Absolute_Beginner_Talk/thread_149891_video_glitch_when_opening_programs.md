---
title: "video glitch when opening programs"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by Video_9 on 2006-03-24
When I open any program I get a split secound video glitch of lines across the screen. I have the newest nvidia graphics driver installed. Anyone know the problem.

by they way im a linux n00b.

---

### Post by trent dillman on 2006-03-24
I'll bet it's that annoying notification effect in Gnome, eh?

Let's start by posting a copy of the file /etc/X11/xorg.conf here and let us take a look.

---

### Post by Video_9 on 2006-03-24
im not sure if its a notification....... its dashed lines in a square type shape, that appears for a millisecond.

---

### Post by trent dillman on 2006-03-24
Yeah, that's probably some eye candy that alerts you to the fact something was opened. It goes away, right? And happens when you minimize too?

edit: your xorg.conf looks fine to me...

---

### Post by Video_9 on 2006-03-24
no, its not that square minimazing animation. this happens almost instantly when i open a program i get random vertial and horzontal white/gray lines that flash for a second in sorta squarish way. like a flicker....

---

### Post by trent dillman on 2006-03-24
Wait a sec.... comment out the last part of your xorg.conf...the whole dri section, then restart gdm

```
sudo /etc/init.d/gdm restart
```

You might have to log in CLI and start/stop though

```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```

---

### Post by Video_9 on 2006-03-24
ok i did that but im still getting the flicker...

---

### Post by trent dillman on 2006-03-24
hmm.... well, you have a slightly different xorg.conf than I do...

        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"

Also try going to 16 bit??

---

### Post by Video_9 on 2006-03-25
that didnt work either. might try to get a picture of it.

---

### Post by trent dillman on 2006-03-25
Try recording it with xvidcap, you can find it at [http://www.jarre-de-the.net/computing/debian/](http://www.jarre-de-the.net/computing/debian/)

Make sure you install libpng2 first, and change the file format to .mpeg

---

