---
title: "Panel is gone"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Xoanan on 2007-06-10
Hi All

I am not quite sure how this happened, but my panels are gone!  It might be because I uninstalled blackdown java, but I am not sure why;  Can anyone help?

Thanx

Xoanan

---

### Post by tito13kfm on 2007-06-11
Hit Alt+F2 and type in gnome-terminal
now type in the following to the terminal
```

gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

```

Edit: I've killed my panels about 4 times already :(  Thank god for this great user community in helping me get things fixed

---

### Post by Xoanan on 2007-06-11
> **tito13kfm said:**
> Hit Alt+F2 and type in gnome-terminal
now type in the following to the terminal
```

gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

```

Edit: I've killed my panels about 4 times already :(  Thank god for this great user community in helping me get things fixed

Thanx for the help; I am actually using Xubuntu which uses the XFCE desktop.  I found the answer in another thread.  

Oddly enough, my system went into overdrive when the panels **weren't** there.  It is okay now, but I do see a little slowdown here.  Its possible I have too much on the panels, but I feel there is more to it than that

Thanx

---

### Post by adityakavoor on 2007-06-13
Thanks tito13kfm

---

