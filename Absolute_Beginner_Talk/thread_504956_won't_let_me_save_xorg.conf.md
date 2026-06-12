---
title: "won't let me save xorg.conf"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by skaspud on 2007-07-19
probably very noob, but i can't copy or save the xorg.conf can som1 help me quick.
it says i don't have permissions necessary...

i  also tried using
sudo cp etc/x11/... etc/x11/xorg.conf.bk
from commmand but it woudln't let me...

---

### Post by Rocket2DMn on 2007-07-19
When you open it to edit, you need superuser privileges.  in terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
ready go!
PS: edit with caution!  you should make a backup first
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
In case you get screwed and stuck in a command line when you restart X (CTRL+ALT+BACKSPACE after you edit the file), run this to restore your backup:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
then you can run
```
startx
``` to restart the X-server (GUI) if you had to recover your backup in the command line interface.

---

### Post by bodhi.zazen on 2007-07-19
You need to open the file with root privilages

```
gksudo gedit /etc/X11/xorg.conf
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

What are you trying to do ?

---

### Post by skaspud on 2007-07-19
tx, trying to enable composite to fix a graphics card/beryl problem.

---

