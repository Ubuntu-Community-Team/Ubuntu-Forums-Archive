---
title: "&quot;sudo gedit /etc/apt/sources.list&quot; is not working"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by secret_force on 2006-08-02
I want to change my sources.list however this happens when I type in the terminal 
ernst@ernst-desktop:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found

Any idea?

edit: I use kubuntu 6.06

---

### Post by givré on 2006-08-02
if you are running kubuntu, kate instead of of gedit should be enough.
gedit is the default text editor in gnome
kate is the one for kde

---

### Post by fourchannel on 2006-08-02
Are you using KDE or Kubuntu? if so then you won't have gedit installted.

however simply replace ```
ernst@ernst-desktop:~$ sudo gedit /etc/apt/sources.list
``` with ```
ernst@ernst-desktop:~$ sudo kwrite /etc/apt/sources.list
``` and you should be OK. =D

EDIT:
Blast! givré beat me to it, haha.

---

### Post by aysiu on 2006-08-02
Never do ```
sudo kate
```

This is better: ```
kdesu kate
``` Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by anaconda on 2006-08-02
use 
sudo nano /etc/apt/sources.list

it works in most linux distros, among them: ubuntu, kubuntu, xubuntu etc...

---

### Post by moma on 2006-08-02
What Edu/X/K/B/Ubuntu needs is a common editor named "editor".

All these distros should create a link to /etc/alternatives/editor.

Ubuntu : ln -s /usr/bin/gedit  /etc/alternatives/editor
Kubuntu: ln -s /usr/bin/kate  /etc/alternatives/editor
etc.

This looks better
$ sudo editor /etc/apt/sources.list 

And maybe preferred dialog should have it too?
$ /usr/bin/exo-preferred-applications

---

### Post by aysiu on 2006-08-02
*nano* is already the common editor.

If I'm not sure what desktop environment a user is using, I'll recommend *nano*. And all the tutorials on my Psychocats Ubuntu site specify the text editor you should use otherwise.

---

