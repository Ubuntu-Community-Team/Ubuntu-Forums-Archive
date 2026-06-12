---
title: "screen 0 not DRI capable"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by jaws31415 on 2008-04-10
I cannot get my desktop to work!  how do I enable this,   or is there any way to get my desktop back.  I'm stuck in a terminal

---

### Post by ibutho on 2008-04-10
If you can see a terminal, login and then run the command "sudo nano /etc/X11/xorg.conf". Look for a line similar to
```
    Load       "dri"
```
and change it to
```
#    Load       "dri"
```
After that run
```
sudo /etc/init.d/gdm restart
```
Does that help?

---

### Post by jaws31415 on 2008-04-10
no there is no read dri in that file

---

### Post by ibutho on 2008-04-11
Out of curiosity, did you try to enable 3d effects? Have you tried changing your video grapics driver to vesa?

---

