---
title: "Probably a very stupid question"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by Twister on 2005-09-29
Hi,

Just installed and lost my train of thought. I installed Hoary and was wondering 2 things.

1. What was the command to start the desktop? (Had a major brainfart and can't remember)

2. I read there was a command to boot directly to the desktop (GUI) but can't find the post now.

A friend helped me but he is now asleep and would kill me if I woke him up. 

Thank you.

---

### Post by Borusa on 2005-09-29
1. startx
2. You use something called gdm - when you've got into gnome, check it's installed (use synaptic).

---

### Post by myha on 2005-09-29
Try this to boot directly into gnome:
```

sudo vi /etc/X11/default-display-manager
add/comment   /usr/bin/gdm

```
or
```
sudo dpkg-reconfigure gdm
```

If you dont have gdm installed do this
```
sudo apt-get install gdm
```
and then
```
sudo dpkg-reconfigure gdm
```

Hope it helps!

---

### Post by Dayylin on 2005-09-29
LOL thanks for helping Twister. He is currently staying at my place and got lost. I wrote down the info he needed but somehow he lost it. It doesn't help that when he did the install that he made some mistakes. He is now running Hoary ok.

---

