---
title: "[SOLVED] Boot problems"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by ShiningWolf on 2008-01-14
Kubuntu starts up, goes through the splash screen and then the standard TTY login screen comes up. I now basically have a console window. There is no graphics environment.  When I dual boot into Windows there is no problem, so I don't think it is hardware related.

The last error message is kinit: no resume image: doing normal boot.

How do I fix this?

---

### Post by Rocket2DMn on 2008-01-14
That message is normal.  Did you just install or upgrade graphics drivers or anything?
To reconfigure X (the GUI), you will have to login at that TTY and run
```
sudo dpkg-reconfigure xserver-xorg
```
This will take you through a bunch of hardware questions, if you don't have an answer to something weird, use the default.  When asked, select your correct video driver (nv for open source nvidia drivers or ati for open source ati drivers).  At the resolutions page select your monitor's max resolution and everything less.
After you finish that run
```
startx
``` and you will be in your GUI.

---

### Post by ShiningWolf on 2008-01-14
Thanks it worked!

Strangely I upgraded nothing.

---

### Post by philinux on 2008-01-14
I think the error message you got might come from hibernation or similar.

---

