---
title: "Server or StandAlone?"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by guysmiley on 2006-03-09
Obviously, I'm a total newb to linux but my question is this:

What is the difference between a server version of linux and a stand alone version?  (i.e. apparently I can use a standalone version as a webserver - would I ever need a server version to run as a webserver - if so, why?)

Thanks for any help you can give me!

gs

---

### Post by mlind on 2006-03-09
usually so called server versions don't necessarily include graphical environment
known as X and no desktop software. server versions also usually include web
services that are somewhat exotic and unneeded for desktop user.

basically, desktop and server versions are collection of different software, services
and customised kernel that would serve the purpose. kernel for server usually
needs to support high memory requirements, but don't need any stuff regarding
to sound card support for example.

you can always build the mixture you want by installing additional software or
removing existing ones. these different versions just make this task easier.

---

### Post by taurus on 2006-03-09
If you plan to login and play around with your machine, then better install the desktop version so you have Gnome.  And of course, you can also install other servers stuff like sshd, ftp, apache, etc.  Just use apt-get to install them...

---

### Post by guysmiley on 2006-03-09
Thanks for the responses and helpfulness.

Your willingness to assist newbs makes me more willing to experiment in the linux world!

gs  :D

---

### Post by Iowan on 2006-03-09
[QUOTE=guysmiley]would I ever need a server version to run as a webserver - if so, why?)
gs[/QUOTE]If your machine has limited resources (RAM in particular) the server version might work where the desktop version chokes.  I have an Ubuntu (file) server running on a P233.  Security is another area - not that the desktop is less secure, but the more "stuff" that's running, the more holes in your armor.

---

