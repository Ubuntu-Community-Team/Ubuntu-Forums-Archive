---
title: "How to disable the laptop mouse"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by perito on 2008-03-12
in win vista, you click FN F9 and you can disable the laptop mouse and only use the USB mouse...
can we do this in Ubuntu?
how?

---

### Post by zxscooby on 2008-03-12
my laptop has a little switch that disables my touchpad

---

### Post by jan quark on 2008-03-12
try this
but make a back up of your xorg file before doing this

[http://ubuntuforums.org/showthread.php?t=429017](http://ubuntuforums.org/showthread.php?t=429017)

to edit your xorg file run 

```
gksudo gedit /etc/X11/xorg.conf 
```


BackUp:
```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

or this
[http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/](http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/)

---

