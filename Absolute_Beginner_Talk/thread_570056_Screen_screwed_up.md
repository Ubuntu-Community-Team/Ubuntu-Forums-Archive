---
title: "Screen screwed up"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by tyraeon on 2007-10-07
Hey guys, I did something kind of stupid. I've been reading on how to work with dual monitors in Ubuntu. My first mistake was not making a backup of my xorg.conf file. I ran the command but it gave me an error so I just thought what the hell and went on editing the file itself.

I added a line I didn't understand to probably the wrong place in xorg.conf, and then I rebooted X. Now when I turn my laptop on it says "Problem with your screen, would you like a server line output?" I can access a terminal-like thing, looks like GRUB, and so I thought I'd run sudo gedit /etc/X11/xorg.conf

However, it says "cannot open display: Run `gedit --help' to see a full list of available command line options.

I can't edit the list to fix my mistake. Any ideas? :[

---

### Post by Dr Small on 2007-10-07
```
sudo nano /etc/X11/xorg.conf
```

Then edit the offending line.

---

### Post by tyraeon on 2007-10-07
Worked great. Thanks for the help!

---

