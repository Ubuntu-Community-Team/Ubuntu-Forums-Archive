---
title: "X server not launchin"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by shinigamicpt on 2006-11-11
i canot access the graphical interface of ubuntu . is it because i did the installation on another comp and run it on another? if so.. how do i remedy the situation ? iam runin ubuntu 6.06 an the gc is nvidia nv4 riva

thank you in advance

---

### Post by taurus on 2006-11-11
Did you install the server version or the desktop (LiveCD) version?  At the prompt, see if you can start X with

```
startx
```
If you get command not found, then you are running the server version so you need to install Gnome with

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by skunkworks on 2006-11-11
If you did indeed install the desktop version, but you did the install on a different computer like you said, are the video cards/chips different?

Try ¨dpkg-reconfigure xserver-xorg¨ and set up your video hardware, mouse, monitor, keyboard, etc. again.

---

### Post by CatKiller on 2006-11-11
Actually, that should probably be ```
**sudo** dpkg-reconfigure xserver-xorg
``` ([https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo))
And you may need to press **Ctrl-Alt-F2** and login there before you are able to enter commands.

The command above will give you an interactive configuration tool to let you select your new graphical setup. You'll probably want to choose the "nv" driver for the time being.

---

### Post by shinigamicpt on 2006-11-11
thanks for all your help i did the

sudo dpkg -reconfigure xserver-xorg 

and everything  went well tq

---

