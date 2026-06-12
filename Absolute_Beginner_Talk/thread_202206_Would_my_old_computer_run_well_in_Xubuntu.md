---
title: "Would my old computer run well in Xubuntu?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by boom2k1 on 2006-06-23
My old computer is a HP Pentium (1) MMX, 64MB RAM, 9 years old.

How do you think it would perform under Xubuntu?

---

### Post by aysiu on 2006-06-23
I think it would perform but still be rather slow.

You'd be much better off doing a server install and then ```
sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic
sudo /etc/init.d/gdm start
``` ...or just using [Damn Small Linux.](http://www.damnsmalllinux.org/)

---

### Post by boom2k1 on 2006-06-23
When you say server, what do you mean by that?

---

### Post by aysiu on 2006-06-23
[QUOTE=boom2k1]When you say server, what do you mean by that?[/QUOTE] There are two installer CDs for Ubuntu.

One is called the **Desktop CD**. It is a live CD that can also install Ubuntu to your hard drive. I can guarantee you even with Xubuntu, you'd have a hard time running this Desktop CD on 64 MB of RAM, let alone using it to install Ubuntu to your computer.

There's another CD called the **Alternate CD** that offers more options (see attached screenshot). One option is the "server install," which can give you a server, but it can also give you a minimal installation (no graphical interface) so that you can tack on only what you want (the command I gave you in my earlier post).

---

