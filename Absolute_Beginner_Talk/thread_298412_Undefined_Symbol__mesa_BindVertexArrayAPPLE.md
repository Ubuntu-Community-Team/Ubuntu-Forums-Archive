---
title: "Undefined Symbol: _mesa_BindVertexArrayAPPLE"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by pvtjohndoe on 2006-11-12
A couple of weeks ago I upgraded to a new version of Compiz by following a thread I found on this forum.

Here's my problem:

After booting up, my screen flashes between the nvidia logo and the command line login three times.  After that I get the following error information:

**Undefined symbol: _mesa_BindVertexArrayAPPLE**

It says this is happening in **libGLcore.so**.

If I comment out the *Load "glx"* line in /etc/X11/xorg.conf, I can use startx to launch Gnome but am without Compiz or video acceleration.

I have found a few people having the same problem but no way to fix it.  Any ideas?

---

