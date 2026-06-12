---
title: "New install"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by ace2002 on 2006-09-14
just installed and looks like I have 2 desktops any help

---

### Post by bodhi.zazen on 2006-09-14
Just delete one. :lol:

Or do you mean your graphics is off? If this is the case, open a terminal and type:
```
sudp cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```

Enter your password. You will not see text on the screen as you type your password. Hit enter.

Now use the three finger salute: Ctrl-Alt-Backspace. This will restart X (your GUI) and bring you to the log-in screen.

HTH

---

