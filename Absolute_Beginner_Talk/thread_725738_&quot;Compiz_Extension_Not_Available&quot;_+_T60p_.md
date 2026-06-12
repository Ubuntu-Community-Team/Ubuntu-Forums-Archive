---
title: "&quot;Compiz Extension Not Available&quot; + T60p + ATI v5200 = ?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by edinwood on 2008-03-16
I have looked forever for a thread this specific... and I've failed to find one. The problem is very similar to a lot of what I've seen before, but nothing has worked for me.

Whenever I try to enable the extra visual effects, I get a small pause, then a window that opens saying that "The Composite extension is not available." And then nothing.

My specs are specified... a T60p with ATI's V5200 graphics card. I've seen help for the other video card that's offered with the model laptop, but nothing with what I have. I want to make sure that what I do is right.

If any more information is needed, I will get it. I just really would like to get this frustrating problem solved! Thanks for the help.

-Eric

---

### Post by joshrobinson on 2008-03-16
have you installed xgl?

---

### Post by edinwood on 2008-03-16
I'm not even sure. My friend did some things with it trying to fix it, but nothing. How would I go about checking or installing it?

---

### Post by joshrobinson on 2008-03-16
```
sudo apt-get install xserver-xgl
```
if it says newest version already installed, then its installed, if not let it install
then run the following command

```
sudo gnome-xgl-switch --enable-xgl
```
restart and try starting compiz now

---

### Post by edinwood on 2008-03-17
Ah that seemed to work! Thanks a bunch! :D

---

### Post by joshrobinson on 2008-03-17
your welcome :)

---

