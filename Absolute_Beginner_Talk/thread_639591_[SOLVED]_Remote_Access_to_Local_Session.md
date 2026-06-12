---
title: "[SOLVED] Remote Access to Local Session?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-12-13
Is it possible to get remote access (via VNC, FreeNX, NoMachine, rdesktop, other) to the local machine session, from a WinXP machine to Xubuntu?

Like how MS's RDP works.
So far I've only been able to find information on connecting to a *NEW* session, but I would like to have access to the LOCAL session as if I was sitting at the terminal.
Is this possible?

---

### Post by ^rooker on 2007-12-13
If my memory is correct, I've done that using FreeNX about 1 year ago - but I can't remember the exact steps to do so. I've followed some basic Howto for FreeNX.

sorry. :(

---

### Post by BassKozz on 2007-12-13
Can anyone please post on this, as far as I know FreeNX will only let you connect to a *NEW* session and not to the local machine session...
Also will FreeNX allow you to logon, so that you can use the computer  headless?

---

### Post by scxtt on 2007-12-13
x11vnc - you can connect to your :0 (i.e. the one on your monitor) w/ it ...
**sudo aptitude install x11vnc** ... you can use your existing vncpasswd w/ it too ...

---

### Post by BassKozz on 2007-12-14
> **scxtt said:**
> x11vnc - you can connect to your :0 (i.e. the one on your monitor) w/ it ...
**sudo aptitude install x11vnc** ... you can use your existing vncpasswd w/ it too ...

AWESOME Thanks scxtt, also I used this HowTo to install: [http://ubuntuforums.org/showthread.php?p=236053](http://ubuntuforums.org/showthread.php?p=236053)

:D

---

