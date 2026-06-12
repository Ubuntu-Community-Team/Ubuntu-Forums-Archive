---
title: "Gnome Broken!"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by zombiepkx on 2007-02-23
I recently installed xserver
(sudo apt-get install xserver-xgl)


and after having huge issues, removed it.
(supo apt-get remove xserver-xgl, or sudo aptitude remove xserver-xgl, can't remember.)

Now, Gnome doesn't load up at all,
I've tried various things.

When I log in, The sounds play, but there's no splash screen, or further activity.

Please help.

:confused:


(I'm on my laptop at school right now, my broken system is at home, with xfpe and gnome on it. GDE daemon.)
I have an nVidia 6800Ultra 512MB video card, and I run AMD64 3800+

6.11 Edgy Eft.

---

### Post by taurus on 2007-02-23
Press <Ctrl><Alt>F2 and log in with your name and password.  Then at the prompt, type

```
sudo dpkg-reconfigure xserver-xorg
sudo shutdown -r now
```

---

### Post by zombiepkx on 2007-02-23
Thanks, I'll try that when I get home :)

---

