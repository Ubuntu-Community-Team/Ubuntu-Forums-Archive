---
title: "I use xgl instead of xserver whats the equivalent of xorg.conf file?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-29
I had to install xgl in order make my ATI graphics card work with Beryl.  I would like to take a look at my xgl configuration file just like i used to look at the xorg.conf file to check out settings.  Where can I look to check this out.

Thanks in advance,

VC

---

### Post by overdrank on 2007-06-29
> **videocheez said:**
> I had to install xgl in order make my ATI graphics card work with Beryl.  I would like to take a look at my xgl configuration file just like i used to look at the xorg.conf file to check out settings.  Where can I look to check this out.

Thanks in advance,

VC

You use the same command in the terminal 
[PHP]gksudo gedit /etc/X11/xorg.conf[/PHP]
Be sure to back it up before  you make any changes!;)

---

### Post by videocheez on 2007-06-29
I just want to understand that I still use xorg.conf file even if i use xgl or maybe i just don't understand whats going on.

---

### Post by overdrank on 2007-06-29
> **videocheez said:**
> I just want to understand that I still use xorg.conf file even if i use xgl or maybe i just don't understand whats going on.

Hi yes you still use the same xorg file, its just xgl for the driver as I understand it. You can check out this link.
[http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl)

:KS

---

