---
title: "open a root window"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Bubs on 2007-04-25
In automatix2 there was a feature it would install that would allow you to right click and open a window with root access.  I just installed feisty and don't want to use automatix2 but I really liked that feature.  does anyone know of something like what I described?

or a way in ubuntu that I can have root privilege without being in the terminal, like a graphical sudo?

---

### Post by Bachstelze on 2007-04-25
To open a nautilus window as root :

```
gksudo nautilus
```

---

### Post by linuxgeekery on 2007-04-25
If you want a graphical sudo, just hit Alt-F2 and type "gksudo command".

---

### Post by eljalill on 2007-04-25
You can also become root in a terminal:
```
sudo su
``` .
Any command you type then is executed as root, but be careful, anything you do is done to root (if you go to home, you are in root's home, not your own etc)

---

### Post by Bachstelze on 2007-04-25
In Ubuntu, it's better to use *sudo -i* instead of *sudo su* for that.

---

### Post by steve.horsley on 2007-04-25
Why's that?

---

### Post by Bachstelze on 2007-04-25
Because it simulates an **i**nitial login instead of just **s**witching **u**ser, thus setting the environment more appropriately. The same thing can be done with *sudo su - root* but *sudo -i* is just shorter to type and more in the Ubuntu spirit of "no root".

---

### Post by steve.horsley on 2007-04-26
Ah. Yes. sudo -i loses any odd environment stuff I've set. Thanks.

---

### Post by Bubs on 2007-07-04
thanks that helps out a lot.  it was a bit complicated without seeing what I was doing (graphically)

---

