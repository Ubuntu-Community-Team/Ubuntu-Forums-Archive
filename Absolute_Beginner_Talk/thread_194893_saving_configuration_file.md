---
title: "saving configuration file"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by phantasmik on 2006-06-12
sorry this is so elementary, however, when you edit a .conf file in terminal, with the "sudo vi" command, how do you save it after editing it

---

### Post by aysiu on 2006-06-12
I prefer ```
sudo nano
``` myself. I never could make head or tail of *vi*.

You can also do ```
gksudo gedit
``` or ```
kdesu kate
``` if you prefer graphical editors.

---

### Post by Phasmagon on 2006-06-12
If you want to just save.
Esc
:
w
If you want to save and exit 
Esc
:
wq

---

### Post by elemental666 on 2006-06-12
try this howto for basic linux operations, it contains a good chapter on VIM (which is a better version of vi): [http://tldp.org/LDP/intro-linux/html/intro-linux.html](http://tldp.org/LDP/intro-linux/html/intro-linux.html)

---

