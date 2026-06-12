---
title: "help with 1280x800 widescreen"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by LeoMan319 on 2006-09-11
ok , so i have a sony vaio s170 and i would like to knwo how to put 1280x800. i installed ubuntu from safe graphic mode because when i try to load the live ccd from the normal setting it give some wierd graphical error right before loading. anyway, what can i do to put 1280x800? a step by step would be nice.. lol

---

### Post by orb9220 on 2006-09-11
Open a Terminal and enter:

sudo dpkg-reconfigure xserver-xorg

Just hit enter for defaults except at screen resolution prompts.

---

### Post by Donshyoku on 2006-09-11
One thing to remember when using the reconfigure utility... use SPACEBAR to select and deselect fields.  If you hit enter on the resolution(s) you want from the list, it will move past that step and you will have to start all over.

---

### Post by bodhi.zazen on 2006-09-11
First, back up xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Now did you try this:
```
dpkg-reconfigure -phigh xserver-xorg
```

If that crashes X:
```
sudo /etc/init.d gdm stop
ctrl-alt-F1 -> now log in
sudo /etc/init.d/gdm stop
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
sudo gdm
```
and re-post.

---

### Post by xander848 on 2006-09-11
Yeah try the advice suggested by bodhi.zazen.(its alot faster as you dont have to go through unneeded steps) That command worked for me on my 1280x800 laptop. 
The only trouble i had was even though I checked 1280x800 it gives me 1280x768 but hey I cant really tell the difference.

---

### Post by LeoMan319 on 2006-09-11
i tired orb's thing and it gave me the same graphical weirdness before loading and just stays on that screen untill i turn off the laptop. i'll try the others.

---

### Post by orb9220 on 2006-09-11
Spacebar Ok was a little sloppy on about enter. Sorry about that.

---

