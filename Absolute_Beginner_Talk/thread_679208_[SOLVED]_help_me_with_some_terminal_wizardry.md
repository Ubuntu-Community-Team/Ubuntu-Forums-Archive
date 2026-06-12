---
title: "[SOLVED] help me with some terminal wizardry"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by h-town on 2008-01-26
I'm following a guide from another forum to fix this pesky mcop error in zsnes. here's what the dude says:

> Search for the following line in /etc/libao.conf:
Code:

default_driver=something

And change it to:
Code:

default_driver=alsa



but when I enter in cd /etc/libao.conf i get this

arrison@The-Zone:~$ /etc/libao.conf
bash: /etc/libao.conf: Permission denied
harrison@The-Zone:~$ 

how am i to fix this?

---

### Post by taurus on 2008-01-26
You need to edit that file so you have to open an editor.

```
gksudo gedit /etc/libao.conf
```

---

### Post by mortsahl on 2008-01-26
Couple of things here ... you can't cd (change directory) to a file

You can cd to its directory -- /etc

You want to edit the file, but it is owned by root, not you, so you have to use sudo to become root for the moment, so enter the command 

sudo vi /etc/libao.conf  
or
sudo pico /etc/libao.conf

of, if you MUST have a gui interface ...

gksudo gedit /etc/libao.conf

---

### Post by h-town on 2008-01-26
woohooo.. thanks a lot. now I'll know what to do in the future for a similar problem.

---

