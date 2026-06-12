---
title: "Boot problem, please assist"
date: 2011-05-29
forum: Any Other OS
---

### Post by germanix on 2011-05-29
Hi all, I have just installed Mint 10 on my sons desktop and when it boots up it automatically brings me to the terminal. How do I get to the normal boot process where the desktop starts? I how do I set it so that in the future the desktop always starts and not the terminal? Help will be greatly appreciated. Thanks!

---

### Post by corncob on 2011-05-29
Its been ages since I used Mint.  If you don't get help here, they do have their own forum:
[http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by bennachie on 2011-05-29
A few further details would help. Do you mean that you have successfully completed a permanent installation to hard disk (ie not an installation within Windows under Wubi), using a liveCD or otherwise?  If so, was that a dual-boot installation (ie, you still have Windows or another version of Linux on the hard disk, and can choose between them at boot-up time)?

---

### Post by corncob on 2011-05-30
Do you mean a terminal window in the GUI that you can close or an actual terminal where you need to login?  If the latter, after logging in, type
```
startx
```
If it says X is already running, try [CTRL][ALT][F7]

---

