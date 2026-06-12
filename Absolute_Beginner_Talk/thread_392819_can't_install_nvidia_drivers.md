---
title: "can't install nvidia drivers"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by iidestined on 2007-03-25
first post!

this is my first experience with linux. I'm having trouble installing the drivers from invidia. I tried to download them from nvidia but when i run the command from the terminal, it says Can't open NVIDIA-Linux-x86-1.0-9755-pkg1.run.

any help would be appreciated. Thanks.:confused:

---

### Post by taurus on 2007-03-25
Use envy.  It's easier and faster.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by elcasey on 2007-03-25
Envy doesn't always work. I have an XFX card which is factory overclocked. Envy does **not** like it.

You can run
```
sudo sh ./NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

But you need to go into TTY (Ctrl+Alt+F1), stop X, then run the command.

---

### Post by taurus on 2007-03-25
I have an XFX GeForce 6800XT and it works perfectly.  But if you want to install it by hand, then there is nothing wrong with that.

---

### Post by iidestined on 2007-03-25
the first reply seems to work fine. thanks for all your help. :)

---

