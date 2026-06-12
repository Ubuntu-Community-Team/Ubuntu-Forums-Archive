---
title: "Installing just ubuntu base system and gnome"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by Dev'olution on 2006-08-12
How would i go about installing the ubuntu base system and the gnome desktop manager on 5.04

Thanks in Advance
5.0.4

---

### Post by richbarna on 2006-08-12
> **WestAussieUbu said:**
> How would i go about installing the ubuntu base system and the gnome desktop manager on 5.04

Thanks in Advance
5.0.4

I think you just install the server, and then "sudo apt-get install gnome" instead of gnome-desktop.

---

### Post by aysiu on 2006-08-12
There is no *gnome-desktop* package. You're probably thinking of *ubuntu-desktop*.

If you want just the basic stuff...

1. Do a server install

2. Enable the Universe repository: ```
sudo nano -B /etc/apt/sources.list
``` Uncomment (remove the # sign from) the Universe lines. Save (Control-X, Y, Enter).

3. Install the basics: ```
sudo aptitude update
sudo aptitude install gnome-core gdm
sudo /etc/init.d/gdm start
```

---

### Post by drtvasudevan on 2006-08-12
dont try that if you have only a live cd.
anyway the default in ubuntu cd is a gnome desktop.
or am i missing something here?

---

### Post by aysiu on 2006-08-12
Well on Hoary you can't install from the live CD anyway. I'm not sure if you can do a server install from the Dapper Desktop CD.

What we're talking about is a minimalist version of Gnome. Ubuntu defaults to a particularly Ubuntu version of Gnome with a lot of bells and whistles. Some people want to use Gnome but add their own bells and whistles... or nothing at all... just the basics.

---

