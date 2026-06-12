---
title: "[SOLVED] Can't load any GUI apps as sudo!!!!"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-10-05
So I tried to install deepdanger, from the .bin file, and had to use 'sudo ./thenameofthefile.bin, it loaded a GUI app that looked like a windows based installer, installed fine, but would not work. It gave me an error, so I when I went to manually remove it from /usr/games/dangerdeep and /usr/share/games/dangerdeep/ in Nautilus as Root, (I used gksudo nautilus), Nautilus loaded, but froze it's screen on my desktop.

I forced quitted it, and then tried several more times. Now Nautilus would not load. So I rebooted, and the same scenario.

How can I get my system to launch GUI applications again ?
HELP!

Dr Small

---

### Post by Pumalite on 2007-10-05
Have you tried rebooting?

---

### Post by Dr Small on 2007-10-05
Yes. 
[quote=Dr Small]So I rebooted, and the same scenario.
[/quote]

---

### Post by Duck2006 on 2007-10-05
sudo sh thenameofthefile.bin

---

### Post by JBAlaska on 2007-10-05
I thought this was the proper way to sudo a graphical program?

```
gksudo "graphical program"
```

---

### Post by Dr Small on 2007-10-05
Got it fixed.
It was my GTK theme messing things up, so I reinstalled the theme and now it works :)

SOLVED!

Dr Small

---

