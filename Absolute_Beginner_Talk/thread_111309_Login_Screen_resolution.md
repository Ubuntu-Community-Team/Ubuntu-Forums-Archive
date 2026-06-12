---
title: "Login Screen resolution"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by confused57 on 2006-01-02
My login screen resolution is so high that I can barely read my username that I
type in.  Would someone be so gracious as to instruct me how to lower the screen
resolution at the login screen?   TIA

---

### Post by poofyhairguy on 2006-01-02
[QUOTE=confused57]My login screen resolution is so high that I can barely read my username that I
type in.  Would someone be so gracious as to instruct me how to lower the screen
resolution at the login screen?   TIA[/QUOTE]

The only way is this command:

```
sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by noob_Lance on 2006-01-02
theres that to perminatly change the resolution... but if your like me on a laptop and have a laptop monitor and external monitor.. once logged in, you can type xrandr in the terminal and it will allow you to choose from a list.

```

lance@testbed:~$ xrandr
 SZ:    Pixels          Physical       Refresh
*0   1280 x 1024   ( 433mm x 347mm )  *75
 1   1024 x 768    ( 433mm x 347mm )   75
 2    800 x 600    ( 433mm x 347mm )   75
 3    640 x 480    ( 433mm x 347mm )   75
 4   1280 x 768    ( 433mm x 347mm )   60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
lance@testbed:~$ xrandr 3 #Will Change my Resolution to 640x480

```

---

